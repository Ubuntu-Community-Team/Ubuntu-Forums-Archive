---
title: "PXE Menu help please."
date: 2010-03-09
forum: Server Platforms
---

### Post by clivebuckwheat on 2010-03-09
Hi  I am following this guide. [http://www.howtoforge.com/setting-up-a-pxe-install-server-on-ubuntu-9.10](http://www.howtoforge.com/setting-up-a-pxe-install-server-on-ubuntu-9.10)

I seem to be have problems with my boot image loading. I put memdisk in the tftpboot folder,  I see at least it is trying to load the boot image. When I DO NOT put the append keeppxe I get the error "failed to load udp stack". If I do put append keeppxe I get "TFTP prefix". The boot images does not load either way. What else can I try?. The boot images is 6 megs and is a Dos based menu system.

Thanks again for any help you can offer me.

below is a copy of the menu.

default vesamenu.c32
Menu Background howtoforge_pxe.png
Menu Title Rob's Pxe Boot Menu

label Install Ubuntu
   menu label ^Install Ubuntu
   menu default
   kernel ubuntu-installer/i386/linux
   append vga=normal initrd=ubuntu-installer/i386/initrd.gz -- quiet

label Ghost Multicast Menu
menu label ^Ghost Multicast Menu
   menu default
   kernel memdisk
   append keeppxe initrd=mcmcd/pxe.img


label Local_drive
   localboot 0
   menu label ^Local Drive

prompt 0
timeout 0

---

### Post by koenn on 2010-03-11
- you have "menu default" for each menu item, that's probably not right

- you could try the installer, see how that works

- /var/log/syslog should contain details about what's happening, so you probably find some clues there

---

