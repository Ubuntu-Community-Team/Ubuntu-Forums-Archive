---
title: "Ubuntu server black screen after instalation and possibly no video drivers"
date: 2016-09-27
forum: Server Platforms
---

### Post by adih2001 on 2016-09-27
Hello! I got an HP proliant ml10 v2 some time ago. At first i had debian linux but i fought to switch to ubuntu server so i did that. The problem is that after instalation is complete when it boots in to the os it show a under like and something above it then it shows an underline (i think that happends.. The first caracter is litterarly cut of the screen due the server not picking up the corrct resolution and this even happends in bios). I read online that i have to boot in a special mode with the "nomodeset" prefix but i have a problem.. the grub launcher thingy dosen't seem to show up and some people suggested to use the instalation usb drive but i dont seem to find any live os on it or boot from hard drive thing.

Note: When i installed the os it prompt me at the ending of the instalation what to install and let what was selected and it plus i selected the ubuntu server base system and a file server

This is one of the problems. There is a another one that ?might happend after i get in to the os (This also happend in debian): As I said above the first caracter will be cut ( I have an 1080p monitor and i am connected via vga) BUT I saw some drivers ( [http://www.pc-freak.net/blog/configure-matrox-graphics-mga-g200-agp-debian-ubuntu-linux/](http://www.pc-freak.net/blog/configure-matrox-graphics-mga-g200-agp-debian-ubuntu-linux/) )for my server video card ( Matrox G200 ) but they they seem to be for desktop (xorg)... I am looking for some drivers for console (non-xorg).

Thank you!

*Sorry for the bad english! This message was written on my phone so sorry for bad formatting*

---

### Post by cariboo on 2016-09-27
Moved. you may get help quicker here.

---

### Post by Bushflyr on 2016-09-28
Does Ctrl-Alt-F1 bring up the terminal window?

---

### Post by adih2001 on 2016-09-29
> **cariboo said:**
> Moved. you may get help quicker here.

Thank you!

> **Bushflyr said:**
> Does Ctrl-Alt-F1 bring up the terminal window?

Ok that actually worked! But the resolution is wrong in console. I was able to enter the server with IPMI and the resolution is 640 x and something... I have an 1080p monitor and the problem was in console (not xorg). I think i need drivers for my Matrox G200.

---

### Post by Bashing-om on 2016-09-29
adih2001; Hello;

Known issues with that graphic card:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1316035) 

a couple of things one can try .

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

