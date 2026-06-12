---
title: "Which version for a new server?"
date: 2012-11-29
forum: Server Platforms
---

### Post by dummzeuch on 2012-11-29
Hi,

I will be building a new server for a small network of Windows XP and Windows 7 machines.
The server will provide the following services:
* Samba primary domain controller
* ssh
* mailserver
* subversion server
* intranet webserver
* web proxy
* dns for internal adresses
Also, I would like to continue using a browser based frontend for administration (currently we use Webmin and I like it)

Our current server, is running Ubuntu Linux Server 10.04.2 LTS. It is showing its age, that's why it will be replaced by the new one.

I consider using the 12.04.1 LTS version and probably the 64 bit version of that.

Is there any reason to prefer either the 32 bit version or the latest (non LTS) version?

---

### Post by darkod on 2012-11-29
For a production server I wouldn't consider non-LTS. I would go with 12.04.

And about 64bit or 32bit, on the download page it still states that 32bit might have more support but I expect 64bit to be able to cover everything you need. Also, if you are using more than 4GB of ram the 64bit version should be able to use it better, although the 32bit comes with PAE kernel which is supposed to be able to use more than 4GB of ram too (I haven't actually tried it).

---

### Post by pkadeel on 2012-11-29
+1 for 12.04.1 LTS for production purposes
No reason to prefer 32bit over 64bit if your hardware is 64bit

---

### Post by Cheesemill on 2012-11-29
+1 for 64-bit.

Also if you must have a WebUI then it might be worth looking at Zentyal which is basically 12.04 with a custom interface.
[http://www.zentyal.org/](http://www.zentyal.org/)

---

### Post by thnewguy on 2012-11-29
I also agree that Zentyal is a good way to go if you want a web interface on top of Ubuntu Server. Zentyal is basically just Ubuntu Server with a web control panel and some pre-configured modules. Really nice way to manage a small office server.

---

