---
title: "Remotely connect to Ubuntu Server Media Change"
date: 2007-08-27
forum: Server Platforms
---

### Post by towel on 2007-08-27
The answer is probably right in front of my face but, I'm just over looking it.

Alright I'm remotely connected to my Ubuntu server but, if I try to install certain packages I get:

Media change: please insert the disc labeled
 'Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)'
in the drive '/cdrom/' and press enter

Is there any way to force it to download the package rather than insert the a disk or comment something out so it doesn't check the cd rom?

 I'm connected remotely to the server and all I can think to do at this point is wget the Ubuntu Server Iso and mount it then try to install the package I want -- whois

Thanks!

---

### Post by soapytheclown on 2007-08-27
> **towel said:**
> The answer is probably right in front of my face but, I'm just over looking it.

Alright I'm remotely connected to my Ubuntu server but, if I try to install certain packages I get:

Media change: please insert the disc labeled
 'Ubuntu-Server 7.04 _Feisty Fawn_ - Release i386 (20070415)'
in the drive '/cdrom/' and press enter

Is there any way to force it to download the package rather than insert the a disk or comment something out so it doesn't check the cd rom?

 I'm connected remotely to the server and all I can think to do at this point is wget the Ubuntu Server Iso and mount it then try to install the package I want -- whois

Thanks!

did u try editing out the cdrom list (usually at the top) of the sources.list??

sudo gedit /etc/apt/sources.list

*edit out lines and close*

sudo apt-get update

sudo apt-get install *package*

:D

---

### Post by towel on 2007-08-27
LOL yay!  Thank you so much!

---

