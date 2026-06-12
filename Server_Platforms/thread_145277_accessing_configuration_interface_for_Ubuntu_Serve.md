---
title: "accessing configuration interface for Ubuntu Server"
date: 2006-03-15
forum: Server Platforms
---

### Post by wgregori on 2006-03-15
I'm a newbie to Ubuntu.  

1. I need to change some network configuration.  Is there an interface to do that.    Other Linux distros I've played with have some sort of VT100 environment that allow me to manage the system (add users, change network info, etc)

Is there any documentation regarding Ubuntu server?

Thanks,
Wayne

---

### Post by kmi on 2006-03-16
```
sudo ifconfig eth0 down
sudo nano /etc/network/interfaces
```
Edit and :
```
sudo ifconfig eth0 up
```
(replace eth0 with the interface you are actually configuring)

Then, considering : [QUOTE=wgregori]I'm a newbie to Ubuntu. 
[/QUOTE]You certainly should have a look at the ["Absolute Beginner Talk"]("http://www.ubuntuforums.org/forumdisplay.php?f=73") section of this forum...

---

