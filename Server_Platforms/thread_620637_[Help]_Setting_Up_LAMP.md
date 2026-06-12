---
title: "[Help] Setting Up LAMP"
date: 2007-11-22
forum: Server Platforms
---

### Post by mrtn400 on 2007-11-22
Notice: I have looked, searched, and googled this topic, and can't find anything that is simple for a beginner to understand, or the tutorial isn't correct to the level that I can't complete it. I posted this topic here because I didn't think people wanted a help request in the Tutorials & Tips section.

First of all I have very little knowledge of any form of linux, but have basically mastered Windows (gasp!), so I should catch on quickly. I used to run a WAMP server, but am currently looking into Ubuntu, because of BIND, and a few other server programs. I know how to install Ubuntu server edition, and can connect to the httpd server through my WAN IP. Everything seemed fine untill I tried to copy my www files from WAMP into /var/www/. It says I need to be root, and don't know the commands to copy a directory using sudo, or how to copy the directory as root using the GUI. Also, if someone could point me into the right direction of a good BIND tutorial, it would be much appreciated.

Thank you for your time,
mrtn400.

---

### Post by dmizer on 2007-11-22
> **mrtn400 said:**
> Everything seemed fine untill I tried to copy my www files from WAMP into /var/www/. It says I need to be root, and don't know the commands to copy a directory using sudo, or how to copy the directory as root using the GUI. 

to copy via command line (preferred):
```
sudo cp /source/directory /destination/directory
```

you can open nautilus (or any gui application) as root, but it's very dangerous to do so.

sorry, don't know any bind tutorials.  for your future reference, here is a list of basic/useful linux command line commands: [http://www.howtoforge.com/useful_linux_commands](http://www.howtoforge.com/useful_linux_commands)

---

