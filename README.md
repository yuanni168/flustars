# flustars(Flutter常用工具类库)
[![Pub](https://img.shields.io/pub/v/flustars.svg?style=flat-square)](https://pub.dartlang.org/packages/flustars)

## [flustars] Flutter常用工具类库。主要对第三方库封装，以便于使用。如果你有好的工具类欢迎PR.  

## 更新说明  
v0.1.5(2018.12.14)  
ScreenUtil新增屏幕适配。
```
//配置设计稿尺寸 默认 360.0 / 640.0 / 3.0
setDesignWHD(_designW,_designH,_designD);

//返回根据屏幕宽适配后尺寸（单位 dp or pt）
ScreenUtil.getInstance().getWidth(100.0);  

//返回根据屏幕高适配后尺寸（单位 dp or pt）
ScreenUtil.getInstance().getHeight(100.0);  

//返回根据屏幕宽适配后字体尺寸
ScreenUtil.getInstance().getSp(12.0);  
```
v0.1.4(2018.11.22)  
ScreenUtil不依赖context获取屏幕数据。  

新增MyAppBar,不需要GlobalKey就能openDrawer。  

## 关于示例
本项目中不包含示例，所有示例均在[flutter_demos](https://github.com/Sky24n/flutter_demos)项目中。  

完整项目[flutter_wanandroid](https://github.com/Sky24n/flutter_wanandroid)，包含启动页，引导页，主题色切换，应用国际化多语言，版本更新等功能。欢迎体验！  

### [flustars](https://github.com/Sky24n/flustars)  
 1、SpUtil       : SharedPreferences 工具类.  
 2、ScreenUtil   : 屏幕适配，获取屏幕宽、高、密度，AppBar高，状态栏高度，屏幕方向.  
 3、WidgetUtil   : 获取Widget宽高，在屏幕上的坐标.  

### [common_utils](https://github.com/Sky24n/common_utils)  
 1、TimelineUtil : 时间轴.(新)  
 2、TimerUtil    : 倒计时，定时任务.(新)  
 3、MoneyUtil    : 精确转换，元转分，分转元，支持格式输出.(新)  
 4、LogUtil      : 简单封装打印日志.(新)  
 5、DateUtil     : 日期转换格式化输出.  
 6、RegexUtil    : 正则验证手机号，身份证，邮箱等等.  
 7、NumUtil      : 保留x位小数, 精确加、减、乘、除, 防止精度丢失.  
 8、ObjectUtil   : 判断对象是否为空(String List Map),判断两个List是否相等. 

## Demo: [flutter_demos](https://github.com/Sky24n/flutter_demos).
## APK: [点击下载v1.0.4](https://raw.githubusercontent.com/Sky24n/LDocuments/master/AppStore/flutter_demos.apk)
## Android扫码下载APK
  ![](https://github.com/Sky24n/LDocuments/blob/master/AppImgs/flutter_demos/qrcode.png)

### Screenshot
<img src="https://github.com/Sky24n/LDocuments/blob/master/AppImgs/flutter_demos/Screenshot_20181003-234414.jpg" width="200">   <img src="https://github.com/Sky24n/LDocuments/blob/master/AppImgs/flutter_demos/Screenshot_20181003-211011.jpg" width="200">   <img src="https://github.com/Sky24n/LDocuments/blob/master/AppImgs/flutter_demos/Screenshot_20180930-012302.jpg" width="200">  
<img src="https://github.com/Sky24n/LDocuments/blob/master/AppImgs/flutter_demos/Screenshot_20180930-012431.jpg" width="200">  <img src="https://github.com/Sky24n/LDocuments/blob/master/AppImgs/flutter_demos/Screenshot_20180919-231618.jpg" width="200">   <img src="https://github.com/Sky24n/LDocuments/blob/master/AppImgs/flutter_demos/Screenshot_20180926-144840.png" width="200">  
<img src="https://github.com/Sky24n/LDocuments/blob/master/AppImgs/flutter_demos/Screenshot_20180919-224204.jpg" width="200">   <img src="https://github.com/Sky24n/LDocuments/blob/master/AppImgs/flutter_demos/Screenshot_20180919-224146.jpg" width="200">   <img src="https://github.com/Sky24n/LDocuments/blob/master/AppImgs/flutter_demos/Screenshot_20180919-224231.jpg" width="200">   

### APIs

```yaml
dependencies:
  flustars: x.x.x  #latest version
```
* #### SpUtil
```
getString
putString
getBool
putBool
getInt
putInt
getDouble
putDouble
getStringList
putStringList
getDynamic
getKeys
remove
clear
isInitialized
```

* #### ScreenUtil
```
getWidth                  : 返回根据屏幕宽适配后尺寸.
getHeight                 : 返回根据屏幕高适配后尺寸.
getWidthPx                : 返回根据屏幕宽适配后尺寸.
getHeightPx               : 返回根据屏幕高适配后尺寸.
getSp                     : 返回根据屏幕宽适配后字体尺寸.
screenWidth               : 获取屏幕宽.
screenHeight              : 获取屏幕高.
screenDensity             : 获取屏幕密度.
appBarHeight              : 获取系统AppBar高度.
statusBarHeight           : 获取系统状态栏高度.
getScreenWidth            : 获取当前屏幕宽.
getScreenHeight           : 获取当前屏幕高.
getOrientation            : 获取当前屏幕方向.
```

* #### WidgetUtil
```
asyncPrepare              : Widget渲染监听，监听widget宽高变化,callback返回宽高等参数.
getWidgetBounds           : 获取widget 宽高.
getWidgetLocalToGlobal    : 获取widget在屏幕上的坐标.
```


### Example

``` dart
// Import package
import 'package:flustars/flustars.dart';

//SpUtil
SpUtil spUtil = await SpUtil.getInstance();
//SpUtil.remove("username");
SpUtil.putString("username", "sky224");
LogUtil.e("username: " + SpUtil.getString("username").toString());

//ScreenUtil
ScreenUtil.getInstance().init(context);

ScreenUtil.screenWidth
ScreenUtil.screenHeight
ScreenUtil.statusBarHeight
ScreenUtil.screenDensity

//WidgetUtil
WidgetUtil widgetUtil = new WidgetUtil();

@override
Widget build(BuildContext context) {
  widgetUtil.asyncPrepare(context, false, (Rect rect) {
     double width = rect.width;
     double height = rect.height;
  });
    return ;
 }

//Widgets must be rendered completely. Otherwise return Rect.zero.
Rect rect = WidgetUtil.getWidgetBounds(context);
double width = rect.width;
double height = rect.height;

//Widgets must be rendered completely. Otherwise return Offset.zero.
Offset offset = WidgetUtil.getWidgetLocalToGlobal(context);
double dx = offset.dx  
double dx = offset.dy

```



