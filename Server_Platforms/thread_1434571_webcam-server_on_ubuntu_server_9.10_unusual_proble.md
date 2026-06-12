---
title: "webcam-server on ubuntu server 9.10 unusual problem"
date: 2010-03-20
forum: Server Platforms
---

### Post by Podmornik on 2010-03-20
I have an unusual problem with mentioned webcam-server on ununtu server 9.10

I installed webcam-server step by step from this page:
[http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server?blog=2](http://hacktivision.com/index.php/2009/06/16/setting-up-an-ubuntu-webcam-server?blog=2)

Then I pluged my Pleomax webcam into computer and started server.
I tested webcam.html on may other computer on the same router and everything is working as it should.

But then I tested the page on my laptop over the wireless connection and something strange is happening because my webcam.html isn't showing picture from the webcam. If I try to access it in this way http:/localhost:8888 I can get a single photo as described in the article.

I tried to access webcam.html from the WAN and the same thing happens.If I try to access it in this way http:/localhost:8888 I can get a single photo as described in the article.

Situation:
My ubuntu server is connected to WRT54GL and on it I have DMZ enabled for the server. If I try to access server from computers connected with LAN connection on the same router everything works well. The soon as I try to connect from WAN I can't see my webcam photo but only the text in my index.html file.

What am I missing? Why on local LAN everything works as it should but if I try to access from outside I can't get my homepage webcam applet working properly?

---

