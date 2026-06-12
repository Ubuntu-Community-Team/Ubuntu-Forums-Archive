---
title: "looking for ip to ip phone software"
date: 2007-11-09
forum: The Cafe
---

### Post by gubemton on 2007-11-09
I am looking for some voip server where I am not forced to use a server. We have non-dynamic ip`s and therefore we wish to call direct from ip to ip without server. The software must be open source.

Please tell me voice software where I can call direct from ip to ip.

---

### Post by intelligentfool on 2007-11-09
its probably overkill, but have you looked at Asterisk? I dont have any experience with it, but i know its open source VoiP, made to scale up to large enterprises, so it should be able to do what your talking about.

[http://www.asterisk.org/](http://www.asterisk.org/)

---

### Post by gubemton on 2007-11-09
I think this is only useful for real phones, developers and such.

I am more looking for something looking like standard messenger Pidgin/Skype, just with the little difference to call ip`s.

---

### Post by williamts99 on 2008-11-27
You can use Ekiga which is installed by default for this.  The following is from the Ekiga help file:

H.323 URL's

H.323 URL's are formatted as such "h323:[user@][host[:port]]"

This permits you to:

    * Call a given host on a port different from the default port which is 1720: h323:seconix.com:1740
    * Call a given user using their respective alias if registered to a gatekeeper: h323:jonita
    * Call a given phone number if you are registered to a gatekeeper for a PC-To-Phone provider, or if that user has an ENUM record associated to an H.323 URL: h323:003210111222
    * Call a given user using their alias through a specific gateway or proxy: h323:jonita@gateway.seconix.com
    * Call an MCU and join a specific room: h323:myfriendsroom@mcu.seconix.com

---

