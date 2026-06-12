---
title: "Sunfire V240 Boot Problems - 7.04"
date: 2007-06-21
forum: Sun Sparc Users
---

### Post by colin_whittaker on 2007-06-21
Hello,

I just finished installing 7.04 on a Sun V240 which now won't boot.
I installed via a network boot and the install went without any difficulties but now I get an Illegal Instruction error when I boot it.

Can anyone shed some light on the causes or even the next steps in troubleshooting this as I am not really that familiar with sun hardware.

Thanks

{1} ok boot

SC Alert: Host System has Reset
Probing system devices
Probing memory
Probing I/O buses

Sun Fire V240, No Keyboard
Copyright 1998-2004 Sun Microsystems, Inc.  All rights reserved.
OpenBoot 4.16.1, 2048 MB memory installed, Serial #61164999.
Ethernet address 0:3:ba:a5:4d:c7, Host ID: 83a54dc7.



Rebooting with command: boot
Boot device: disk0  File and args:
SILO Version 1.4.13
boot:
Allocated 8 Megs of memory at 0x40000000 for kernel
Uncompressing image...
Loaded kernel version 2.6.20
Loading initial ramdisk (6331681 bytes at 0x103E002000 phys, 0x40C00000 virt)...
Illegal Instruction

---

### Post by colin_whittaker on 2007-06-21
Just to follow up to this.
I tried a hard power cycle and it now seems to work fine.

I am left wondering if that behaviour was caused from previously trying to boot a cdrom.

---

