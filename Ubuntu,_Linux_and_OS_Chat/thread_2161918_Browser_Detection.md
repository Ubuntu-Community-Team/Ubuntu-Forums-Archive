---
title: "Browser Detection"
date: 2013-07-12
forum: Ubuntu, Linux and OS Chat
---

### Post by winrat on 2013-07-12
I bought a DVR for security use. It is browser controlled over the LAN with a static IP address. Trouble is it only works with Windows -IE/Firefox/Chrome  or whatever you want.
It is supposed to also work over the internet with iPhone, Android Symbian etc.
,
So what is it that prevents Linux/OSX from accessing it? Same browsers - apart from IE - but they cannot connect to the page.

Any ideas gratefully accepted

---

### Post by mr john on 2013-07-12
When you open any web page your browser sends a small message to the server indicating which browser you are using and which operating system you are using.  This is called the user agent string.  When I visit a website my browser sends the following information to the server:

> 
**Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/27.0.1453.116 Safari/537.36**


You can see there that I'm using Windows NT6.1 which is Windows 7. If I wanted to trick the website into thinking I'm using Linux I would need to change the message that my browser sends. Thankfully there are browser plugins that allow you to do that.


User agent switcher for firefox should be able to trick the server into thinking you are on Windows:

[https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/](https://addons.mozilla.org/en-US/firefox/addon/user-agent-switcher/)


However, if the DVR software uses an ActiveX plugin to display the cameras, which many do, you will have to use Windows.

---

