---
title: "i can't install ubuntu 7.10 on sun blade 150"
date: 2007-10-24
forum: Sun Sparc Users
---

### Post by jocumer on 2007-10-24
Hi for all! 
i'm trying to install ubuntu 7.10  in SUN Blade 150, but apper this error.

Allocate 8 Megs of memory at 0x40000000 for kernel
loaded kernel version 2.6.22
loading initial ramdisk (5844610 bytes at 0x4E002000 phys, 0x40C00000 virt)...
Memory Address not Aligned 
ok

i read all post in this forum, but not find to the answer.

bios version is:

release 4.6 version 5 create 2002/06/03 16:49
OBP 4.6.5 2002/06/03 17:13
POST 2.0.1 2001/08/23 16:50
OBDIAG 4.6.5 2002/06/03 16:50

tanks for all.

---

### Post by jcastill on 2007-11-26
Check if you have the latest OBP. I will try to bring out a sunblade150 to try to test it.

---

### Post by Nunu on 2007-11-27
does the sun blades have bios based memory allocation?

---

### Post by jmunkham on 2008-01-16
I had the same problem and I found several solution suggestions. Like set the boot device order, disconnecting the floppy drive. Non worked, I didn't even have a floppy.

The only thing that worked was to pull the power plug. It seems that after the box have been running Solaris there's still something in there that a reset or a LOM power off can't clean. After pullong the cable and power back on it booted just fine on the Ubuntu CD.

cheers, \\Jan

---

### Post by clarkritz on 2008-04-02
I second that.  Shutting down, pulling out the power cord, and then booting from the CD worked.  

Of course now, I can't configure the Xserver....

---

### Post by dspiteri on 2008-04-04
Get to the boot prompt with stop-A or break. At the OK prompt:

setenv boot-device cdrom
reset-all

---

### Post by ubu_for_umm on 2008-04-12
Also .. after the setenv tip above ... you should do:

install ide=nodma .. that worked for me on the 4 150s I installed Ubuntu on.

---

### Post by ronbd on 2008-05-21
Stick with 6.06. The kernel that shipped with 7.x does not honor the ide=nodma flag and your disk will get corrupted as DMA will be enabled anyway. And 6.06 doesn't have the openssh bug :)

---

### Post by |{urse on 2008-05-21
Wow just saw this, yeah 6.06, I just had this exact same problem and nothing made it happy 7*wise. =/

---

### Post by balkor on 2008-05-22
I just wanted to say thank you to 
dspiteri
for the post on the this issue for it had truly helped me on a 

SunFire 280R UltrSPARC III+

I was getting the:
ERROR: Last Trap: Illegal Instruction
Error -256

even after I flashed openboot to most current available

so thank you again from a SPARC noob

---

