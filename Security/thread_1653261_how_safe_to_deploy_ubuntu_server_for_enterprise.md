---
title: "how safe to deploy ubuntu server for enterprise"
date: 2010-12-26
forum: Security
---

### Post by aliyagoob on 2010-12-26
Dear Folks, 

I am deploying ubuntu server for the first time in our enterprise, but  I have a number of concerns since free open source

1.	official Support for the OS ?
2.	Security issues incurred due to freeware software in Data Center
3.	Patch management
4.	Vulnerabilities as an outcome of the freeware.
5.	Non functioning of the services or dependencies.

your kind responses are highly appreciated

---

### Post by CharlesA on 2010-12-26
1. You can pay for support.
2. All software has vulnerabilities, but most of the time they are patched fairly quickly.
3. Applying the latest updates is just an apt-get away.
4. See #2.
5. What do you mean?

---

### Post by cariboo on 2010-12-26
Just to add to what CharlesA said, Wikipedia uses Ubuntu servers, and Google uses a customized version of Ubuntu server.

From the sounds of it, you haven't set up a server yet, I would suggest you create a vm and do some testing, just to get your feet wet, before setting up the actual system, that way there aren't any surprises, when you do the real installation.

[Turnkey Linux]("http://www.turnkeylinux.org") has quite a view Ubuntu based appliances, that will allow you to test various setups out.

---

### Post by bodhi.zazen on 2010-12-26
> **aliyagoob said:**
> Dear Folks, 

I am deploying ubuntu server for the first time in our enterprise, but  I have a number of concerns since free open source

1.	official Support for the OS ?
2.	Security issues incurred due to freeware software in Data Center
3.	Patch management
4.	Vulnerabilities as an outcome of the freeware.
5.	Non functioning of the services or dependencies.

your kind responses are highly appreciated

Sounds as if you are very new to Linux servers.

1. I suggest you contact Canonical for (professional) support.

2. I suggest you start reading on Linux security, start with the stickies, including Apparmor, then read:

[http://www.debian.org/doc/manuals/securing-debian-howto/](http://www.debian.org/doc/manuals/securing-debian-howto/)

3. [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

Then read on hardening any server you install (apache, php, mysql, etc, etc).

I would avoid ftp if at all possible.

---

### Post by HermanAB on 2010-12-27
Howdy,

Linux is Linux is Linux...

In other words, provided that you know what you are doing, it doesn't matter too much which distribution you use, since deep down, it is all the same.  It is only the desktop fluff that is slightly different.

---

