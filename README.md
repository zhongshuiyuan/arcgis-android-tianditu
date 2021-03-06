# arcgis-android-tianditu

[![Download](https://api.bintray.com/packages/wshunli/maven/arcgis-android-tianditu/images/download.svg)](https://bintray.com/wshunli/maven/arcgis-android-tianditu/_latestVersion)
[![Build Status](https://travis-ci.org/wshunli/arcgis-android-tianditu.svg?branch=master)](https://travis-ci.org/wshunli/arcgis-android-tianditu)
[![Author](https://img.shields.io/badge/Author-wshunli-0E7FBF.svg)](http://www.wshunli.com)
[![GitHub license](https://img.shields.io/github/license/wshunli/arcgis-android-tianditu.svg)](https://github.com/wshunli/arcgis-android-tianditu/blob/master/LICENSE)

Library for displaying and caching tianditu layers based on ArcGIS for Android

[基于 ArcGIS for Android 的天地图图层显示及缓存(中文版)](README_zh_CN.md)

![vector](screenshot/vector.jpg) | ![image](screenshot/image.jpg) | ![terrain](screenshot/terrain.jpg)
:-: | :-: | :-:
vector | image | terrain

## Dependency

### ArcGIS for Android Dependency

Install the needed dependencies and the ArcGIS Runtime SDK for Android (ArcGIS Android SDK)  binaries from Bintray Esri repostiory.

```groovy
repositories {
    jcenter()
    // Add the Esri public Bintray Maven repository
    maven {
        url 'https://esri.bintray.com/arcgis'
    }
}
dependencies {
    // Add ArcGIS Runtime SDK for Android dependency
    implementation 'com.esri.arcgisruntime:arcgis-android:100.3.0'
}
```

For more information : [Install and set up—ArcGIS Runtime SDK for Android](https://developers.arcgis.com/android/10-2/guide/install-and-set-up.htm)

### arcgis-android-tianditu Dependency

Install arcgis-android-tianditu library.

```groovy
dependencies {
    implementation 'com.wshunli.map:arcgis-android-tianditu:2.0.0'
}
```

Check out [arcgis-android-tianditu releases](https://github.com/wshunli/arcgis-android-tianditu/releases) to see more unstable versions.

## Quick Start

### Permission

The library requires three permissions:

``` XML
<uses-feature android:glEsVersion="0x00020000" android:required="true" />

<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.ACCESS_FINE_LOCATION" />
```

So if you are targeting Android 6.0+, you need to handle runtime permission request before next step.

Note that OpenGL is included as a feature.

### Simple usage snippet

``` Java
MapView mMapView = findViewById(R.id.mapView);
ArcGISMap map = new ArcGISMap();
TianDiTuLayer vec_c = new TianDiTuLayerBuilder()
    .setLayerType(TianDiTuLayerTypes.TIANDITU_VECTOR_MERCATOR)
    .build();
map.getBasemap().getBaseLayers().add(vec_c);
mMapView.setMap(map);
```

### Cache tianditu tile layers

Just specify the cache path

``` Java
MapView mMapView = findViewById(R.id.mapView);
ArcGISMap map = new ArcGISMap();
String cachePath = Environment.getExternalStorageDirectory().getAbsoluteFile() + "/TianDiTu100Cache";
TianDiTuLayer vec_c = new TianDiTuLayerBuilder()
    .setLayerType(TianDiTuLayerTypes.TIANDITU_VECTOR_MERCATOR)
    .setCachePath(cachePath)
    .build();
map.getBasemap().getBaseLayers().add(vec_c);
mMapView.setMap(map);
```

File will be cached to the specified path

## More

Find more details about arcgis-android-tianditu in [sample](https://github.com/wshunli/arcgis-android-tianditu/tree/master/sample).

## 10.X Version

For ArcGIS for Android 10.2.9 and the older version in [README.10.X](README.10.X.md)

## License

    Copyright 2017 wshunli

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
