---
title: "/etc/default/grub file does not exist"
date: 2011-06-10
forum: Server Platforms
---

### Post by AestheticD on 2011-06-10
Hi everyone,

Due to a motherboard issue, I need to edit a parameter in the "etc/default/grub" file.

However, the problem is, that file doesn't exist.

Grub does seem to be installed, I can get into grub from the command line etc.

This is a fresh install of Ubuntu Server - 10.04.2 LTS

Brand new box, no previous installs of anything, no other operating systems etc.

Is there somewhere else that file could reside ? I tried find -name '*grub*' and got plenty of files, but none are the one that I need.

Is there someway to generate this file ?

I remember when installing from the CD it asking about grub, but I don't recall which option I chose, it was whichever one was the default.

If anyone can help me at all, I would very much appreciate it. This thing won't reboot right after power loss etc until I can edit that value... which at the moment seems to not exist....

Btw, I'm not a total linux noob but far from an expert, so I may need any answers "dumbed down" a bit.

Thanks a million in advance



EDIT (more info):

It seems that I have regular "grub" and not "grub2" installed... I'm assuming that is part of the problem ?

My version: grub-install (GNU GRUB 0.97)

Does this version of grub allow you to edit options etc ?

Specifically, what I need to do, is edit this value: GRUB_CMDLINE_LINUX_DEFAULT

I need to add "reboot=a" to this line.

---

### Post by ZuOverture on 2011-06-10
Grub1 doesn't use /etc/default/grub, it uses /boot/grub/menu.lst instead. You can also wish to install Grub2 - it may be done quite easily with your Ubuntu CD.

---

