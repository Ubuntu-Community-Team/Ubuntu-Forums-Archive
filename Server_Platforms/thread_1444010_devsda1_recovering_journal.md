---
title: "/dev/sda1: recovering journal??"
date: 2010-03-31
forum: Server Platforms
---

### Post by vannguyen0 on 2010-03-31
So I insatlled Ubuntu Server 9.10 (64bit) on a VMware ESXi.  I then cloned the installation.  On the one that I cloned, I noticed this on boot:

fsck from util-linux-ng 2.16
**/dev/sda1: recovering journal**
/dev/sda1: clean, 170/24096 files, 36423/96356 blocks
fsck from util-linux-ng 2.16
**/dev/sda3: recovering journal**
/dev/sda3: clean 21/91392 files, 14489/365478 blocks
fsck from util-linux-ng 2.16
/dev/sda4: clean, 54686/243840, 310391/973940 blocks

It happens every time I reboot the VM.  I do not notice that same message on the original VM.  Is this something I need to be concerned with?

---

### Post by vannguyen0 on 2010-04-05
So after some troubleshooting, I figured out that I only get this message if I install vmware tools.  

If I do not install vmware tools, the system boots up without the

**/dev/sda1: recovering journal**
....
**/dev/sda3: recovering journal**

messages.

Anyone else using Ubuntu Server in a ESXi environment???

---

### Post by bartcramer on 2010-05-17
I don't know the solution... but at least I can confirm the problem (although it doesn't seem like a real problem so far). It only does it for the /home partition, for me at least. 

I also noticed, with vmware tools installed, that it doesn't need to recover it when I reboot immediately (hence not much writing to /home).

---

### Post by windependence on 2010-05-17
It's not a "problem" at all, it's a forced file system check to make sure of the integrity of the virtual disk. It does not hurt a thing, in fact, it's a good thing&#8482;

-Tim

---

