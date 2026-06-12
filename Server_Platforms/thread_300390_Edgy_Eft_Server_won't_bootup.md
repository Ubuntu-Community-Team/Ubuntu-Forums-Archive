---
title: "Edgy Eft Server won't bootup"
date: 2006-11-15
forum: Server Platforms
---

### Post by CorePoint on 2006-11-15
Hi,

i have a problem with Ubuntu 6.10 on my Server.

I have a very old Computer. Pentium 1 MMX, 128 MB Ram, Ati Mach 64.

I installed Ubuntu 6.10 Server on it with no problems. But on the first reboot Grub is loading, then Display shows "Starting up..." and then teh PC restarts. Can anybody help me to fix this problem?

Sorry for my bad english.

---

### Post by CorePoint on 2006-11-16
Same with Dapper Drake :(

The big problem is i don't get any error message, so i don't know what i can do.

---

### Post by CyberX on 2006-11-16
Hi.
The server kernel only runs with Pentium Pro or later (i686), not with Pentium I or equivalent. You have to replace the kernel or reinstall with the Alternate CD instead.

---

### Post by imjustabill on 2006-11-24
As previously stated, the Ubuntu Server kernel is compiled for 686 machines. The easiest way to fix this is to boot the installation CD in rescue mode, and run the following:

```

apt-get install linux-386
apt-get remove linux-server

```

Reboot without the CD and everything should work.

---

### Post by esaym on 2007-01-02
> **imjustabill said:**
> As previously stated, the Ubuntu Server kernel is compiled for 686 machines. The easiest way to fix this is to boot the installation CD in rescue mode, and run the following:

```

apt-get install linux-386
apt-get remove linux-server

```

Reboot without the CD and everything should work.

I just had to do the same thing to get the lamp server running on an amd k6-2 350mhz box.  I would have never thought that the problem was from the wrong kernel.

Thank you.  You're a life saver!!!

---

