---
title: "Help with OpenSSL"
date: 2009-08-01
forum: Server Platforms
---

### Post by feeblminds on 2009-08-01
Hi, really hoping someone can help me as I have spent hours trying to fix this and my head is a bit of a mess after.

Basically I have a ubuntu server which I host my companies website on. The last IT person put an SSL certificate on the site which we host ourselves. Problem is that in Internet Explorer 7, when you visit the website IE asks

'The wesbite you want to view requests identification. Please choose a certificate.' 

There are no certificates to choose + I dont really want it asking as it will frighten away customers. 

I'm reasonably knowledgable with Linux and know that the we are using opensll on a ubuntu server and are using apache to host the site.

Anybody any suggestions, im guessing its a setting in the config file but I dont know where the config file is either???

I would really appreaciate any adivce. 

ps the website is [https://www.topquoteuk.com](https://www.topquoteuk.com)

---

### Post by LepeKaname on 2009-08-02
Check this link, it may be helpful:

[http://httpd.apache.org/docs/2.0/ssl/ssl_howto.html#allclients](http://httpd.apache.org/docs/2.0/ssl/ssl_howto.html#allclients)

---

### Post by feeblminds on 2009-08-03
Hey, thanks a lot for that, seems I just needed to change the SSLVerifyClient setting to none!  

Thank you very much.

---

