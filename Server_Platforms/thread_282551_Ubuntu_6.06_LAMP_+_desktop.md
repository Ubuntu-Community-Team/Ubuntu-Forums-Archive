---
title: "Ubuntu 6.06 LAMP + desktop"
date: 2006-10-22
forum: Server Platforms
---

### Post by taylor.morley on 2006-10-22
Hello Everybody,

I recently installed Ubuntu 6.06 LAMP server, set everything up.
I decided to install Firestater instead of manually configuring iptables. I decided to go the apt-get install ubuntu-desktop route.

everything installed, and I rebooted the machine, only to be left at a command line. I started X, and setup firestarter and removed some of the un-needed programs installed with the desktop (OpenOffice, audio/video stuff, and what not). I rebooted the machine and it still does not boot into the GUI, any ideas?

Also, is it possible to use vnc to log in remotely after the machine has been rebooted? I've played around with the pre-installed remote desktop, but that only works if I'm currently logged into the machine. If I reboot the machine remotely I'm unable to remote desktop into the machine until I'm logged in locally.

Thanks in advance,
Taylor

---

### Post by Soul_Est on 2006-10-24
I don't know if will help u any but you need to install Xorg first.
I believe the command to install it is:

> sudo apt-get install xserver-xorg-core

This was what I used when I tried to do a custom installation of Ubuntu for everyday use. Needless to say I forgot the alsa and a few other parts of the underlying framework. ](*,) ](*,) ](*,) 

If this works for you please post back here or send me a PM stating how you got everything working. I'm hoping to do a customization How-to for Edgy Eft and putting together a LAMP server is something I'd like to consider including. How this works for you and good luck!

---

### Post by taylor.morley on 2006-10-24
Well I've gotten everything working, turns out the gui wasn't completely installed, or I removed an important peice when I was uninstalling the extra stuff I didn't need. So I reinstalled the desktop with this command:
> apt-get install ubuntu-desktop

and everything works fine.

---

