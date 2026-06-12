---
title: "Are you interested: Linux Auto Hardware Installer Daemon Project ?"
date: 2007-12-10
forum: The Cafe
---

### Post by frenchn00b on 2007-12-10
Linux Auto Hardware Installer Daemon Project
-----
what it is: Auto Hardware Installer Daemon Project is a daemon that makes your life easier, and gives you all in Linux to save your time. Linux is not always meant to be complicated, and can be simple as just plug to install a new element of hardware.
 
  
Install:
apt-get install lahid
rpm lahid
and the /etc/init.d/lahid start at boot, let the process run
  
  
Context:
- you are for instance playing a movie
- you feel like you need one new hardware for your system,
- go to the mall, buy it,
- back home simply plug
- and continue what you were doing before like nothing happens
X message to display :0.0 => xmessage " Device label X just installed. Click OK"
       * the daemon see the new hardware
       * control its references : fabricant, idproduct, deviceBus, ...
       * go to [www.linuxdriver.org](www.linuxdriver.org) / [ftp://linuxdriver.org/drivers/model](ftp://linuxdriver.org/drivers/model)...
       * download the driver in the /tmp
       * unpack it
       * verify the kernel in its /boot/configX
(if necessary propose to recompile (please do not tell me that it is not that difficult and it could be automatic, but we try to avoid recompiling the kernel)
       * and start installing the driver / modules (./configure ; make ; make install way) located in the automatic hardware installer of the downloaded package
       * and continue what you were doing (just clicking on OK on the display 0.0)
       * Driver Installed: You save 20 min of time (and life mb. ;) )

---

### Post by Lostincyberspace on 2007-12-10
I don't want to get Laid. 
:lolflag:
Just couldn't resist.

---

### Post by EXCiD3 on 2007-12-10
I wouldnt mind having this. It would be one of those things that were time savers. This is essentially a Linux version of Plug n Pray?

---

### Post by smartboyathome on 2007-12-10
Is this just an idea, or is it already availabe somewhere?

---

### Post by Tharkun on 2007-12-10
I would like this.

---

### Post by ~LoKe on 2007-12-10
Sounds neat, though I've had no problems thus far. Are you sure it's possible?

---

### Post by tinman6700 on 2007-12-11
sounds like it could really help a long time Microsloth user get up to speed

---

### Post by khurrum1990 on 2007-12-11
It would be excellent if we had it, its gets boring to configure new hardware all the time.

---

### Post by Majorix on 2007-12-11
I wouldn't want to have this from someone with 0 posts: I don't want my comp to be ruined by a french**n00b**. My PC is up and running without such a daemon anyways.

---

### Post by el_ricardo on 2007-12-11
i find it painfully obvious that this would be the best project to truely get the general public into using linux, i really hate buying hardware, plugging it in and it taking a week to get working properly, people are so used to the mainstream OS's seeing hardware and automatically configuring it for them that its no wonder people are afraid to try out linux distros

I think that with more and more PC manufacturers having ubuntu (or similar) as an option, eg dell; such a daemon is bound to be included in the kernel in the next 1-2 years anyway. Now is definatly the time for someone to get to work on it!

---

