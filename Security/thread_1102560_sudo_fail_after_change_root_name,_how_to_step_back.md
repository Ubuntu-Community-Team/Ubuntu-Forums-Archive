---
title: "sudo fail after change root name, how to step back ?"
date: 2009-03-21
forum: Security
---

### Post by NiTR0 on 2009-03-21
Hello,
	
I installed ubuntu version 8.10 as a server. I wanted to change the name of the root. But since nothing works, how come back as before?

I did this with the following command

**$ sudo useradd -l root sysroot**

Since when using SUDO he said

**sudo: no passwd entry for root!**

How to turn back now without SUDO and root only with the user during installation of ubuntu?

**Please help me ! i'm very new to this world ...:-(**

---

### Post by NiTR0 on 2009-03-21
Thank! 

I'm finally found solution ... :-)

**Boot in recovery mode**

1- ESC when GRUB appear
2- Choice Kernel .... (Recovery Mode) and press E
3- Choice Kernel line and add at the end init=/bin/bash and press Enter
4- Press B and at the prompt type mount -rw -o remount /
5- Rename root user
6- pwconv
7- reboot your server

---

