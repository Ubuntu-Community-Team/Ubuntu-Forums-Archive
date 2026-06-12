---
title: "ajaxterm (apache2) configuration"
date: 2010-12-28
forum: Server Platforms
---

### Post by chrismyers on 2010-12-28
Hi Guys,

I have successfully tested ajaxterm on the apache default website on port 80 based on this help:

[https://help.ubuntu.com/community/AjaxTerm](https://help.ubuntu.com/community/AjaxTerm)


For one moment. please assume that I already have a default website on port 80 that I do not want to disturb, for example:

[http://test](http://test)

Can anyone tell me if I can configure to access ajaxterm from here:

[http://test/term](http://test/term)

My apache knowledge is a bit rubbish. Can anyone help please?

Many thanks,

Chris.

---

### Post by stmiller on 2010-12-29
ajaxterm runs on a special port, so it won't work on port 80 without setting up an apache proxy.

Ex: [http://localhost:8022/](http://localhost:8022/)


I've got a short how-to for shellinabox here if that helps, using a proxy to get it on a standard port:

[http://scottlinux.com/?p=1195](http://scottlinux.com/?p=1195)

---

### Post by MarkoCro on 2011-03-21
AjaxTerm is slow and ugly. What I use is [Shell In A Box]("http://code.google.com/p/shellinabox/"). Here is my howto for setting it up on Ubuntu with https and HTTP authentication:

[http://www.techytalk.info/remote-cli-access-to-ubuntu-pc-using-web-browser-through-authenticated-https/]("http://www.techytalk.info/remote-cli-access-to-ubuntu-pc-using-web-browser-through-authenticated-https/")

Cheers!

---

