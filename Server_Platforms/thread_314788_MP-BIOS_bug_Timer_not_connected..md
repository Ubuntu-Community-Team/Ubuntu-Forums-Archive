---
title: "MP-BIOS bug: Timer not connected."
date: 2006-12-08
forum: Server Platforms
---

### Post by OttifantSir on 2006-12-08
I am running a 
Compaq Proliant ML370/G2
P3 1.26 Ghz
1.5 GB RAM
2x SCSI 36.7 GB HD
2x SCSI 67.2 GB HD
2x Compaq 64-bit/66 Mhz Dual Channel Wide Ultra 3 SCSI-cards
HP NC3163 Fast Ethernet (10/100)
ALi PCI-to-USB 2.0
CT 4160 soundcard
48x CD-ROM (Compaq SC-140C)

When I insert the 6.06 Live CD and restart, it will go to the boot-menu and start loading the kernel (although there's a visual disturbance, a blue, jagged line, at the middle of the screen)
It works for a little while, then I get this error message:

[4294671.956000] ..MP-BIOS bug:8254 timer not connected to IO-APIC

The same happens when I try the 6.10 Server CD. The only difference are in the numbers at the beginning of the error message:

[4294672.620000] ..MP-BIOS bug:8254 timer not connected to IO-APIC

When I used the 6.10 Alternate Install (for machines with less than 192 MB RAM) I could acces the install program. I went as far as to partitioning before cancelling. (Not yet finished backing up files)

Anyone know what this message means? Is it something that will make me dependent on Windows also in the future? (Not being able to install to this server because of some weird hardware configuration)

Much obliged for any help, as I have never done a server-install and only used Ubuntu for about a month.

Edit: I have an old Red Hat Linux CD (6.2) lying around somewhere. I can try this later and see if it gives any error messages if it's desirable.

---

### Post by OttifantSir on 2006-12-14
I have just now tried running the RedHat 6.2 installation CD. It didn't display this bug.

---

### Post by OttifantSir on 2006-12-18
Noone seen this before?

Or am I to understand that this is a problem that's unsolvable at the moment?

---

### Post by livinginx on 2007-01-09
Press F6 to bring up the box boot options.  Add: noapic
to the end of it.

---

