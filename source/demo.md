title: hybrid phongap app 演示
speaker: Theo Wang
url: https://github.com/ksky521/nodePPT
transition: move
files: /js/demo.js,/css/demo.css,/js/zoom.js
theme: color

[slide]
# 前沿前端技术汇总
> 大前端需要具备那些技能？<br>怎样炼就一线的前沿攻城师攻略？<br>你觉得还有那些前沿技术?<br>请markdown添加上，nodeppt运行。

[slide]

# hybrid app 开发 

``node phongap cordova html5 React.js``

<small>整理：shangwenwu </small>

[slide]

# 搭建Android开发环境 {:&.flexbox.vleft}

- node npm *vs:0.8 - 0.10.25* {:&.rollIn}
- cordova
- jdk 及配置环境变量 
- Aapche Ant 及配置环境变量 
- Android SDK
- ADT

    `iOS 需在苹果机上搭建 ... `

[slide]
# cordova 创建一个项目
[subslide]

* cordova create hello com.shj.helloworld helloapp {:&.rollIn}
	<pre><code class="markdown">第一个 hello 是文件夹的名称；om.shj.helloworld 是app id，第二个 helloapp是工程的名称，也是应用的名称。</code></pre>
* cd hello
	`进入工程文件夹`

============

* 添加平台支持
<pre><code class="markdown">
	 $ cordova platform add ios
	 $ cordova platform add amazon-fireos
	 $ cordova platform add android
	 $ cordova platform add blackberry10
	 $ cordova platform add firefoxos
	 $ cordova platform add wp7
	 $ cordova platform add wp8
	 $ cordova platform add windows8
	 
	`此处选择cordova platform add android`
</code>
</pre>
============
* 添加插件支持
<pre><code class="markdown">
  `调用手机功能API接口`
  `基本设备资讯 （设备 API）：`
   $ cordova plugin add org.apache.cordova.device 
  `网路连接和电池事件：`
   $ cordova plugin add org.apache.cordova.network-information 
   $ cordova plugin add org.apache.cordova.battery-status
</code>
</pre>
* API接口地址
<pre><code class="markdown">
  `http://docs.phonegap.com/zh/3.4.0/guide_cli_index.md.html`
</code>
</pre>
[/subslide]
[slide]
## 项目目录结构
----
<div style="float:left;">
<img src="/mljg.png" title="目录结构" />
</div>
<div style="float:left;margin-left:50px;font-size:18px; line-height:25px; width:650px;  text-align:left;">
	<p>
		<h3>www目录：</h3>
		前端开发的静态文件<br>
        重点考虑：单网页应用、路由规范、本地信息存储、设计应用框架结构、页面切换过场、跨域请求数据机制、响应式规范、React业务模块组件、公共模块组件、文件加载机制、部署时压缩合并打包机制等。
		<hr />
		<h3>platforms目录：</h3>
		cordova自动生成的平台（ iOS Android ... ）结构<br>
        重点考虑：了解原生应用的配置文件（ adnroidManifest.xml config.xml .... ）、桌面ICON、启动初始界面等。
		<hr />
		<h3>plugins目录：</h3>
		调用手机底层功能插件,需了解接口API。
		<h3>config.xml：</h3>
		app基本信息配置 
	</p>
</div>



[slide style="background-image:url('/img/bg1.png')"]

# 前端文件开发完成后与Android iOS合并 {:&.flexbox.vleft}
```html
cordova build
cordova build android
cordova build ios
```

[slide]

# 真机调试  {:&.flexbox.vleft}
```html 
cordova run build android
cordova run build ios
```
# Ripple Emulator安装及调试 
```html 
npm install -g ripple-emulator
ripple emulate
```

[slide]
# 浏览器运行 {:&.flexbox.vleft}
```html 
cordova serve android
```
# 在模拟器上安装测试应用 
如android平台，应先将 android 模拟器启动并打开
```html 
cordova emulate android
```

[slide]
## 生成apk程序目录
----

```platforms\android\build\outputs\apk
```

[slide]
# hybrid app开发框架篇 {:&.flexbox.vleft}
1. ionic {:&.rollIn}
2. reapp
3. 其它：Ratchet/Lungo/QuoJS/...

[slide]
## Ionic
> ionic是一个专注于用WEB开发技术，基于HTML5创建类似于手机平台原生应用的一个开发框架。目前绑定的与`angularJS`和SASS。这个框架的目的是从web的角度开发手机应用，基于PhoneGap的编译平台，可以实现编译成各个平台的应用程序。
> 视频教程：http://www.ionic.wang/course-index.html

[slide]
## Reapp
> Reapp是一款使用`React`来开发混合应用的开源框架，为开发者提供了他们开发所需的一切，其中包括各式模块的集合、UI工具包、引导应用的CLI，以及一个预配置的构建服务器，支持Android、iOS。起先，Reapp的构建并不是以成为一个框架为目的，相反，它是作为一个UI工具包开始的。Reapp很简单，你甚至可以只是用其中的UI工具包就能构建出一款应用。


<pre><code class="markdown">如果Ionic框架可以看成Angular与cordova的结合，那么Reapp可以看成是reactjs与cordova的结合。
</code></pre>



[slide]
## hybrid框架对比
<img src="/reapp.jpg" title="框架对比" />

[slide]
#Webpack 模块加载神器
> Webpack 是德国开发者 Tobias Koppers 开发的模块加载器。Instagram 工程师认为这个方案很棒, 似乎还把作者招过去了。在 Webpack 当中, 所有的资源都被当作是模块, js, css, 图片等等..因此, Webpack 当中 js 可以引用 css, css 中可以嵌入图片 dataUrl。对应各种不同文件类型的资源, Webpack 有对应的模块 loader, 比如 CoffeeScript 用的是 coffee-loader, 其他还有很多:http://webpack.github.io/docs/list-of-loaders.html

[slide]
# 前端开发技术篇 {:&.flexbox.vleft}
1. 单网页应用 {:&.rollIn}
2. 路由规范
3. 本地信息存储
4. 设计应用框架结构
5. 页面切换过场
6. 跨域请求数据机制
7. 响应式规范
8. React业务模块组件
9. 公共模块组件
10. 文件加载机制
11. 部署时压缩合并打包机制

[slide]
# 推荐网址篇  {:&.flexbox.vleft}

醉牛前端http://f2er.club/

大前端http://haomou.net/

CSS3动画库
http://daneden.github.io/animate.css/

基础样式
http://necolas.github.io/normalize.css/

[slide]
# 前端提升篇  {:&.flexbox.vleft}
1. 第一阶段：库/框架选型（重点） {:&.rollIn}
> react、angular、bootstrap、backbone、animate.css、zepto、jquery、underscore、normalize.css、fontAwesome...
2. 第二阶段：自动化构建工具：压缩合并打包..（优化）
> fis3、gulp、grunt、webpack...
3. 第三阶段：js/css模块化开发<br>
> sea.js、require.js、less、sass、webpack、common.js....
4. 第四阶段：合作开发部署<br>
> git、svn...
5. 第五阶段:开发测试<br>
> tower、jira...

<br>
摘录：<br>
http://www.w3cplus.com/front-end-engineering-part-1.html

[slide]
#小常识 {:&.flexbox.vleft}
##windows系统建立热点
> cmd命令依次输入<br>
netsh wlan set hostednetwork mode=allow ssid=mywifi1111 key=12345678<br>
netsh wlan start hostednetwork<br>
netsh wlan stop hostednetwork<br>

`备注:ssid为热点名称,key为热点密码。可自行更改`

[slide]
#常见的跨域方式
1. 使用iFrame访问另一个域。 然后再从另一个页面读取iFrame的内容。jquery等有一些封装。
2. jsonp。需要服务器支持。使用script src动态得到一段java代码。是回调页面上的js函数，参数是一个json对象。
3. 设置http头，Access-Control-Allow-Origin：*
4. 服务器代理。如，服务器写一个url的处理action。其参数是一个url。这个服务器会用参数拼凑一个url,用httpclient库去执行url，然后把读取的内容再输出到http客户端。


[slide]
#nginx反向代理实现跨域
<pre><code>$('button').click(function(){
       $.get('partners/json',function(result){ //url地址域名在nginx中配置
          $('div').html(result);
       });
    });
</code></pre>

<pre><code>server{
	listen8000;
    location/ {
       includeuwsgi_params;
       uwsgi_passunix:/tmp/testFlask2.sock;
    }
    location/partners {
       rewrite^.+partners/?(.*)$ /$1 break;
       includeuwsgi_params;
       uwsgi_passunix:/tmp/testFlask1.sock;
    }
}
</code></pre>