# DaydreamSample-GVR1.0.3  
DevFest Kansai 2016 GoogleVR Session SamplePJ  

|target|version|
|:--|:--|
|Unity|5.4.3f1|
|Google VR SDK for Unity|1.0.3|
|PC|Windows10 x64|

# 実装方法
## Google VR SDK for Unity パッケージをインポートする  
メニューから  
`Asset > Import Package > Custom Package`  
を選択し、Google VR SDK for Unityパッケージを選択する。  
![01](https://raw.githubusercontent.com/wiki/scarviz/DaydreamSample-GVR1.0.3/images/001.png)
  
Importボタンを押下する。  
![02](https://raw.githubusercontent.com/wiki/scarviz/DaydreamSample-GVR1.0.3/images/002.PNG)

もし、下図のようなダイアログが出たら、「Import Package」ボタンを押下する。  
(下図は左が切れているが、一番左のボタン)  
![03](https://raw.githubusercontent.com/wiki/scarviz/DaydreamSample-GVR1.0.3/images/003.PNG)

Importボタンを押下する。  
![04](https://raw.githubusercontent.com/wiki/scarviz/DaydreamSample-GVR1.0.3/images/004.PNG)


## ステレオカメラ化
Projectビューから  
`Asset > GoogleVR > Prefabs > GvrViewerMain`  
を選択する。  
![05](https://raw.githubusercontent.com/wiki/scarviz/DaydreamSample-GVR1.0.3/images/005.PNG)

GvrViewerMainを、HierarchyビューにD&Dする。  
![06](https://raw.githubusercontent.com/wiki/scarviz/DaydreamSample-GVR1.0.3/images/006.PNG)


## レチクル(照準点)対応
### 照準対象物の配置
照準の対象物としてCubeを配置する。  
メニューから  
`GameObject > 3D Object > Cube`  
を選択する。  
![07](https://raw.githubusercontent.com/wiki/scarviz/DaydreamSample-GVR1.0.3/images/007.png)

### GvrReticleの配置
レチクル(照準点)が表示されるように、GvrReticleを配置する。  
Projectビューから  
`Asset > GoogleVR > Prefabs > GvrReticle`  
を選択する。  
![08](https://raw.githubusercontent.com/wiki/scarviz/DaydreamSample-GVR1.0.3/images/008.PNG)

GvrReticleを、Hierarchyビューの  
`Main Camera`  
の中にD&Dする。  
![09](https://raw.githubusercontent.com/wiki/scarviz/DaydreamSample-GVR1.0.3/images/009.PNG)

### Main CameraにPhysics Raycasterコンポーネントを追加する
視線の先をレイキャストするために、Main CameraにPhysics Raycasterコンポーネントを追加する。  
HierarchyビューのMain Cameraを選択し、Main CameraのInspectorビューで、Add Componentボタンを押下し、  
`Physics Raycaster`  
を選択する。  
選択すると下図のようにPhysics Raycasterコンポーネントが追加される。  
![10](https://raw.githubusercontent.com/wiki/scarviz/DaydreamSample-GVR1.0.3/images/010.PNG)

### Event Systemの追加
対象物(Cube)にレチクルが当たったかどうかのイベント用にEvent Systemを追加する。  
メニューから  
`GameObject > UI > Event System`  
を選択する。  
![11](https://raw.githubusercontent.com/wiki/scarviz/DaydreamSample-GVR1.0.3/images/011.png)

HierarchyビューのEvent Systemを選択し、Event SystemのInspectorビューで、Add Componentボタンを押下し、  
`Gaze Input Module`  
を選択する。  
選択すると下図のようにGaze Input Moduleコンポーネントが追加される。  
Input Moduleが重複すると意図せぬ動作をするため、Standalone Input Moduleコンポーネントのチェックボックスのチェックを外しておく。  
![12](https://raw.githubusercontent.com/wiki/scarviz/DaydreamSample-GVR1.0.3/images/012.PNG)


### 対象物にEvent Triggerコンポーネントを追加する
対象物(Cube)にレチクルが当たったかどうかのトリガー用にEvent Triggerコンポーネントを追加する。  
HierarchyビューのCubeを選択し、CubeのInspectorビューで、Add Componentボタンを押下し、  
`Event Trigger`  
を選択する。  
選択すると下図のようにEvent Triggerコンポーネントが追加される。  
もし、レチクルが当たった時、外れた時、クリックされたときなどのイベント処理を実装したい場合は、「Add New Event Type」ボタンで追加してやる。ここでは詳細な説明は省略する。  
![13](https://raw.githubusercontent.com/wiki/scarviz/DaydreamSample-GVR1.0.3/images/013.PNG)

## 実行する
実行すると、中央にレチクル(白い点)が表示され、Cubeに当たると、円になり、外れると点になることが分かる。  
下図ではレチクルが分かるように、Cubeに赤色のMaterialを付けている。  
![14](https://raw.githubusercontent.com/wiki/scarviz/DaydreamSample-GVR1.0.3/images/014.PNG)