---
title: "Funny Weird Ubuntu One not installed error"
date: 2010-03-28
forum: Ubuntu One (CLOSED)
---

### Post by d.justins on 2010-03-28
justin@CastleHouseLinux:~$ ubuntuone-client-applet
The program 'ubuntuone-client-applet' is currently not installed.  You can install it by typing:
sudo apt-get install ubuntuone-client-gnome
ubuntuone-client-applet: command not found
justin@CastleHouseLinux:~$ sudo apt-get install ubuntuone-client-gnome
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntuone-client-gnome is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
justin@CastleHouseLinux:~$ 

I'm not sure how to move from here.

---

### Post by joshuahoover on 2010-03-29
> **d.justins said:**
> justin@CastleHouseLinux:~$ ubuntuone-client-applet
The program 'ubuntuone-client-applet' is currently not installed.  You can install it by typing:
sudo apt-get install ubuntuone-client-gnome
ubuntuone-client-applet: command not found
justin@CastleHouseLinux:~$ sudo apt-get install ubuntuone-client-gnome
[sudo] password for justin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntuone-client-gnome is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
justin@CastleHouseLinux:~$ 

I'm not sure how to move from here.

It sounds like you may either have the PPA version, in which case we removed the ubuntuone-client-applet and replaced it with ubuntuone-preferences. If you look at our installation page for the PPA you can see more details on where things are at now:

[https://one.ubuntu.com/support/installation/](https://one.ubuntu.com/support/installation/)

Thank you,

Joshua

---

