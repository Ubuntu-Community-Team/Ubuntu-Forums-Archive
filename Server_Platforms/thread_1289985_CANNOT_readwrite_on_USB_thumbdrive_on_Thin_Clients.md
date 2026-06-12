---
title: "CANNOT read/write on USB thumbdrive on Thin Clients!"
date: 2009-10-13
forum: Server Platforms
---

### Post by AlexanderDGreat on 2009-10-13
Hi I already followed these:

[https://wiki.ubuntu.com/EnableLTSP5LocalDevices](https://wiki.ubuntu.com/EnableLTSP5LocalDevices)
[https://wiki.ubuntu.com/DebugLocalDev](https://wiki.ubuntu.com/DebugLocalDev)

Whenever I plug it in my thin client, it mounts on desktop as usb-sdb1, but I can't read/write to it. It says, cannot allocate memory. File Operation is hanging! I tried it on a different servers, different machines (Intel Atom, old Celeron, HP dv2000 laptop), changed USB sticks, I looked everywhere! It's so frustrating!

PS But in Virtualbox, I can USE the f*#&kng thing!

---

### Post by AlexanderDGreat on 2009-10-15
Hi isn't anyone out there experiencing the same problem? I think it's the way my LTSP-Clients Were Built. Maybe I need to reBuild them?

Are these messages normal if you're building a client? 

I: Retrieving aptitude
W: Couldn't download package aptitude
I: Retrieving base-files
I: Validating base-files
I: Retrieving base-passwd
I: Validating base-passwd
I: Retrieving bash
W: Couldn't download package bash
I: Retrieving bsdutils
W: Couldn't download package bsdutils

NOTE the: W: Couldn't download package...

Maybe that's why my USB drives aren't readable? And my display is sometimes wrong resolution? Anyway, if you receive messages like these, couldn't you just UPDATE your CHROOT environment and everything will be fixed?

Thanks.

---

### Post by AlexanderDGreat on 2009-11-01
It seems this is a bug [https://bugs.launchpad.net/ltsp/+bug/415952](https://bugs.launchpad.net/ltsp/+bug/415952) - But I solved it now.

---

