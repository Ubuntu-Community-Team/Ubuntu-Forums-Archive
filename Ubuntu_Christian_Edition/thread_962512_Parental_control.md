---
title: "Parental control"
date: 2008-10-29
forum: Ubuntu Christian Edition
---

### Post by roald on 2008-10-29
Hi!
I've been trying Ubuntu and UbuntuCE for some days, and am really impressed. Will probably switch from Windows for most of my computers. Unfortunately my kids love games that only run on Windows...

Anyway: I've been searching the internet and this forum for information if it is possible to set up an UbuntuCE installation with 2 network interfaces, one towards the internet and the other towards my home network. What I basically want to accomplish is this:
* have all internet traffic from my home network pass through this computer so that the traffic will be filtered by Dansguardian, without having to adjust proxy-settings on the other computers in my house

As far as I can judge the above is a combination of a firewall and Dansguardian, but I guess it should be possible to tweak a standard UbuntuCE installation to accomplish this.

Thanks in advance :)

Roald

---

### Post by moz44 on 2009-12-15
roald: good to know you want to switch to ubuntu. There is a program in Ubuntu called 'wine' (stands for WINdows Emulator) which can run some windows executables. I'd recommend you going to their website (wine.org) and check to see if the apps you want to run in Ubuntu are supported. In the case that the games your children like to play are not supported(cant run) in linux then I would suggest installing VirtualBox which lets you install windows under linux, so for sure all app will run. You can know more in their website: [www.virtualbox.org](www.virtualbox.org)

For a one-time parental control configuration in your LAN, I recommend you configure your router to block those sites with sexual, violent content based on a list of words (it may depend on the features available in your router). I have a Linksys WRT54G and it works out that way. However, I am sure there are open source alternatives to parental control. We just need to research sourceforge.net a bit.

check this app: [http://draxus.org/upload/Parental%20control.tar.gz](http://draxus.org/upload/Parental%20control.tar.gz) it is runnable under ubuntu only

---

### Post by david_kt on 2009-12-15
> **roald said:**
> Hi!
I've been trying Ubuntu and UbuntuCE for some days, and am really impressed. Will probably switch from Windows for most of my computers. Unfortunately my kids love games that only run on Windows...

Anyway: I've been searching the internet and this forum for information if it is possible to set up an UbuntuCE installation with 2 network interfaces, one towards the internet and the other towards my home network. What I basically want to accomplish is this:
* have all internet traffic from my home network pass through this computer so that the traffic will be filtered by Dansguardian, without having to adjust proxy-settings on the other computers in my house



Please let us know exactly what games, it might be able to run on CE out of the box as well. E-Sword is windows program, run out of the box in CE.

From version 6 (Karmic Koala) onward, CE has capability to use two network cards, out of the box. Please check "Internet connection sharing" menu on dansguardian gui.

DK

---

