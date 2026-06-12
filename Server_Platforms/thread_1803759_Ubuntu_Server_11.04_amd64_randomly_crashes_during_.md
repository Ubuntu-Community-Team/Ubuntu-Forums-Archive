---
title: "Ubuntu Server 11.04 amd64 randomly crashes during installation, i386 works fine"
date: 2011-07-13
forum: Server Platforms
---

### Post by keger on 2011-07-13
Hello everyone,

I am trying to install Ubuntu Server (64 bits) on a machine that boasts an AMD Athlon II X4 630 on a MSI 785GM-P45 motherboard and 4 x 2GB of Corsair XMS3 DDR3 PC3 10666.

The installation of Ubuntu Server 11.04 amd64 randomly crashes with a kernel panic (freeze + flashing keyboard lights) at various steps of the installation process (anywhere from the keyboard configuration to the user creation).
The Ubuntu Desktop 11.04 amd64 LiveCD runs perfectly fine.
The installation of Ubuntu Server 11.04 i386 works perfectly fine and the system is stable. Unfortunately, I absolutely need a 64-bit OS (because of the custom software the machine is supposed to run).
The installation of Ubuntu Server 10.04 amd64 works fine but then the system is very unstable. It crashes a few seconds after startup, even if there is no specific human action (see screenshot for details).

I'm pretty sure the issue isn't related to:
- the RAM (all the modules passed a memtest86+ successfully),
- the motherboard (it has been replaced and it hasn't solved anything),
- the hard drive (I've tried with two different hard drives - one Hitachi one Western Digital, both 1.5TB - with two different SATA cables on two different SATA ports of the motherboard).

The only hardware plugged into the computer are the keyboard and an external DVD drive (for the Ubuntu server disc - I also tried with a USB key). Network card and graphic card are embedded on the motherboard. I've tried playing with the BIOS settings (deactivating ACPI, AMD "Cool'n'Quiet", default and safe-mode settings, etc.) with no luck. I've also tried to mess with the Ubuntu disc boot options ("noacpi" and such) but with no luck either.

Any idea what the problem is? Any 10.04+ Ubuntu server amd64 version would work.

Thanks!

---

