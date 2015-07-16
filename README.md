# NGUIAdapter
NGUI的多分辨率适配

主流分辨率的宽高比：

Iphone4s 640*960，宽高比为0.6667。

Iphone5 640*1136，宽高比为0.5634。

Ipad mini 768*1024，宽高比为0.75。

Android机的分辨率宽高比大部分在0.5634到0.6667之间。

UI适配规则：以640*960为基础，进行高度适配。

在Ipad上宽度过大的机型上用固定的贴图遮挡住黑边。

在Iphone5上我们增加摄像机的正交大小（Camera.orthographicSize）来放大显示范围。使得1136-960的内容也能显示出来。但这样就导致几个问题：

1、之前在顶部的UI以及在底部的UI显示位置不对。

2、背景图显示不全。

3、ScrollView中的内容位置显示不对。

在NGUI下，适配需要做一下几步。

1、调整Camera.orthographicSize的值。

2、上层UI按钮之类的位置分为上中下，程序与美术定好。

3、背景贴图乘以Camera.orthographicSize来缩放。

4、SoftClip裁剪区域按上中下三种方式对齐，然后在把高乘以Camera.orthographicSize。

至此可以做到以高度来适配不同的分辨率。

