---
title: "Blank screen after server post-installation reboot"
date: 2011-10-04
forum: Server Platforms
---

### Post by mralternative on 2011-10-04
Hi!

I've been searching heavily about my problem, and though it seems like a common issue (and addressed a few times), it still seems to be an issue for me...

You see, I've installed Ubuntu Server 11.04. My first installation ran smoothly, and booted normally, however the old HDD (a 60GB Seagate from 2004..) promptly died, so I installed a new 500GB Seagate. The installation runs fine until the GRUB boot loader. However, upon reinstalling (for the umpteenth time), the GRUB boot loader finally works.

Once the system reboots, however, I'm faced with a blank/black screen. Choosing to boot fron the first hard disk via the CD splash screen results in the system staying on (I refrain from saying "hanging" since I'm not sure if the system has seized..) "Booting from First Hard Disk..."

I've tried reinstalling a few times to no avail - I've even tried different monitors. I installed OpenSSH aswell, since I intend to use this computer as a file server and install Samba later. So I figured that, perhaps, it is just a graphics card error and the system is actually booting just fine. However, the computer doesn't appear on my router. :/

The computer continues to do this, despite reformatting the system drive and reinstalling a number of times now.

Any help would be *greatly* appreciated.

EDIT: I've also tried booting from the CD with NOMODESET aswell to no avail

---

### Post by lcman on 2011-10-04
> **mralternative said:**
> Hi!

I've been searching heavily about my problem, and though it seems like a common issue (and addressed a few times), it still seems to be an issue for me...

You see, I've installed Ubuntu Server 11.04. My first installation ran smoothly, and booted normally, however the old HDD (a 60GB Seagate from 2004..) promptly died, so I installed a new 500GB Seagate. The installation runs fine until the GRUB boot loader. However, upon reinstalling (for the umpteenth time), the GRUB boot loader finally works.

Once the system reboots, however, I'm faced with a blank/black screen. Choosing to boot fron the first hard disk via the CD splash screen results in the system staying on (I refrain from saying "hanging" since I'm not sure if the system has seized..) "Booting from First Hard Disk..."

I've tried reinstalling a few times to no avail - I've even tried different monitors. I installed OpenSSH aswell, since I intend to use this computer as a file server and install Samba later. So I figured that, perhaps, it is just a graphics card error and the system is actually booting just fine. However, the computer doesn't appear on my router. :/

The computer continues to do this, despite reformatting the system drive and reinstalling a number of times now.

Any help would be *greatly* appreciated.

EDIT: I've also tried booting from the CD with NOMODESET aswell to no avail

I believe you didn't set the bootable flag on your /boot partition while partitioning your drives during installation.

Without the bootable flag, Grub won't be able to determine which drive to boot from. Do that and see if the problem gets solved.

---

### Post by mralternative on 2011-10-05
That doesn't make sense to me, as Id set the GRUB to just boot into ubuntu server, as it is the only OS, and just used Guided partitioning. I did this aswell with the old 60Gb drive, which booted properly.

---

### Post by lcman on 2011-10-05
> **mralternative said:**
> That doesn't make sense to me, as Id set the GRUB to just boot into ubuntu server, as it is the only OS, and just used Guided partitioning. I did this aswell with the old 60Gb drive, which booted properly.

Do a manual partition and try to partition like in the pics. Use LVM and raid if you want!

If it doesn't work, you definitely have faulty hardware!

---

### Post by mralternative on 2011-10-05
I'll try that. Thank you!

---

### Post by mralternative on 2011-10-05
EDIT: double check instructions and found i made a mistake. will try again

---

