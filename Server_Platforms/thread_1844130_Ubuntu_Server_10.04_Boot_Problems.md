---
title: "Ubuntu Server 10.04 Boot Problems"
date: 2011-09-14
forum: Server Platforms
---

### Post by ciantrius on 2011-09-14
Hi,

I've just hit a bit of a problem that I can't see how to get round, any suggestions would be appreciated.

I've setup one of my apache hosts to have an ssl password, for which I am getting a prompt during boot. The problem is I can't enter the password ?! I'm using an old desktop with a ps2 keyboard, the keyboard works fine in the BIOS and the Num Lock etc turn on the appropriate lights. I just can't get past the password prompt.

Is there anyway of bypassing apache2 at startup and then launching it later ?????

Any thoughts would be gratefully received as I really could do with the server being up right now.. 

Cheers, Jon.

---

### Post by oldos2er on 2011-09-14
Moved to Server Platforms.

---

### Post by WatchDogx on 2011-09-24
I have the same issue. Apache asks for my ssl cert passphrase. I put in the password and press enter and nothing happens. I cannot get past the password prompt. None of the key combinations ive tried will get past other than control alt del which just restarts.

---

### Post by ibutho on 2011-09-24
One option you have, is to boot your system using an ubuntu live cd (or usb), chroot into your Ubuntu installation (the root partition installed on the hard drive) and run
```
sudo update-rc.d -f apache2 remove
```
After that reboot and make the desired changes you need in order for apache to work the way you want.

---

