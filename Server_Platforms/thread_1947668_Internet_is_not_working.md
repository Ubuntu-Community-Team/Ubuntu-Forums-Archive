---
title: "Internet is not working"
date: 2012-03-27
forum: Server Platforms
---

### Post by dakshinraj on 2012-03-27
Hi,

I have recently installed ubuntu server 11.10, using the ISO image i installed packages for Ubuntu desktop i tried to install, it was not there,

I typed [COLOR=Red]apt-get install ubuntu-desktop [/COLOR][COLOR=Black]but it is showing not available, but in my server internet is working. When i ping google.com it is working but for downloading it is not connecting to online repository..

suggest me... no proxy or firewall is used
[/COLOR]

---

### Post by FreeD01 on 2012-03-27
Have you enabled universe and multiverse repositories? Check this:

[http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html](http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html)

---

### Post by CharlesA on 2012-03-27
> **dakshinraj said:**
> Hi,

I have recently installed ubuntu server 11.10, using the ISO image i installed packages for Ubuntu desktop i tried to install, it was not there,

I typed [COLOR=Red]apt-get install ubuntu-desktop [/COLOR][COLOR=Black]but it is showing not available, but in my server internet is working. When i ping google.com it is working but for downloading it is not connecting to online repository..

suggest me... no proxy or firewall is used
[/COLOR]

Run this:

```
sudo apt-get update
```
```
apt-cache search ubuntu-desktop
```

> **FreeD01 said:**
> Have you enabled universe and multiverse repositories? Check this:

[http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html](http://www.ubuntugeek.com/how-to-enable-the-universe-and-multiverse-repositories-in-ubuntu-804-hardy.html)

You shouldn't have to enable any other repos because the packages in question are in the main repos. Besides, that document is for Hardy and the OP is using Oneric.

---

