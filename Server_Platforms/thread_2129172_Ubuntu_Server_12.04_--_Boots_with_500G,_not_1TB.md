---
title: "Ubuntu Server 12.04 -- Boots with 500G, not 1TB?"
date: 2013-03-25
forum: Server Platforms
---

### Post by DaveHightower on 2013-03-25
OK, I am stumped...


I recently set up an Ubuntu Server on an old SS4200-E;  since it is **completely** headless (no way all all to connect a display, no console port, nothing), I installed Ubuntu Server 12.04 on a different system, then moved the hard drive to the SS4200.


Here's the odd thing--when I installed the server (core + openSSH) on an old Deskstar 500G drive, the system booted fine, came up -- and I am able to SSH to it.


I then installed the server (exact same options) on a Caviar Black 1TB -- and it doesn't boot.  I see disk activity, then nothing.  Does not respond to Pings, can't SSH.


I moved the drive back to my build system -- first it said the ELF header was smaller than expected.  I reinstalled, tried again -- no joy.  Moved it back, it was stuck at the grub boot screen.


I did the fix at [http://ubuntuforums.org/showthread.php?t=1598854](http://ubuntuforums.org/showthread.php?t=1598854), and on the build system it boots immediately.  Reinstall in the SS4200;  no joy again.


Am I doing something wrong?

---

### Post by dino99 on 2013-03-25
thats let me wondering about that bios : is it able to identifie large hdd ?

---

### Post by Bashing-om on 2013-03-25
Nother thought, is the processor pae and sse2 enabled(required now for ubuntu, else use other versions of 'buntu) ?

---

### Post by NetworkNerd7 on 2013-03-25
Possibly your BIOS may not support that large of a hard drive.

---

### Post by dcstar on 2013-03-27
This is a NAS device with a specific list of tested devices, if the 1TB drive is NOT on the list then there is no guarantee that it will work:

[http://download.intel.com/support/motherboards/server/ss4200-e/sb/ss4200e_thol_14.pdf](http://download.intel.com/support/motherboards/server/ss4200-e/sb/ss4200e_thol_14.pdf)

---

### Post by Elfy on 2013-03-27
*Thread moved to **Server Platforms**.*

---

