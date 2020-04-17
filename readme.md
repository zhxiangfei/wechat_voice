## 实现流程： ##
#### 一、 公众号配置 
1.JS安全域名配置：登陆微信公众平台：公众号设置 -> 功能设置 -> JS安全域名，域名写到根域名就行，把下载的txt文件放到域名对应的根目录下

2.配置ip白名单

#### 二、微信接口 
用到了'startRecord', 'stopRecord', 'playVoice', 'uploadVoice', 'translateVoice'五个接口。

先调用 startRecord 开始录音，再调用 stopRecord 停止录音，会返回一个音频的本地Id，把录音追加的Html录音列表中，方便播放录音，使用 playVoice 播放录音列表中的录音，再使用 uploadVoice 把录音上传到微信服务器上，会返回微信服务器上的serverId（感觉上传录音没有使用到），通过使用本地音频id去识别语音

#### 三、代码说明 
1、Wechat.php 此类主要是获取accessToken和jsapiTicket

2、Wxmedia.php  此类是返回语音识别的配置信息

#### 补充说明 ####

/public/wxtxt文件夹下的access_token.txt和jsapi_ticket.txt存放的是access_token和jsapi_ticket的信息以及各自的过期时间。

参考博客 [微信开发之JS-SDK + PHP实现录音、上传、语音识别](https://www.cnblogs.com/zxf100/p/12718661.html "微信开发之JS-SDK + PHP实现录音、上传、语音识别")