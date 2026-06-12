---
title: "Upgraded from 2.6.24-16 to 2.6.24-17 kernel - now LVM/LUKS will not boot!"
date: 2008-05-29
forum: Security
---

### Post by kevdog on 2008-05-29
I'm really frustrated.  I again upgraded kernels from 2.6.24-16 to 2.6.24-17, and now the login for the LVM/LUKS process during boot hangs after typing the password.  I previously posted a question regarding this issue, but is whole disk encryption vulnerable to kernel upgrades? I can only boot into the 2.6.24-16 kernel.  Are there any instructions how to resolve this?

---

### Post by hyper_ch on 2008-05-29
nope, for me kernel upgrades work fine... but then I don't use lvm...

---

### Post by kevdog on 2008-05-29
This Hardy release is killing me -- kernel is broken -- random lockups, upgrades kill the kernel -- I'm really starting to hate this.

---

### Post by hyper_ch on 2008-05-29
:(

---

### Post by tubezninja on 2008-05-29
Using the GRUB boot menu, you should be able to boot back onto the 2.6.24-16 kernel.

---

### Post by kevdog on 2008-05-29
Yes, I can boot back into the old kernel, but due to some Acer/recent kernel incompatibility (that exists to this day even in the most recent vanilla kernel) the system randomly freezes.  On this machine Im headed back to Gutsy after a total wipe and reinstallation.  I actually thought some of the cosmetic changes in Hardy were decent compared to Feisty (and I'm not one to be really interested in GUIs and menus and compiz and such).  Launchpad has others reporting random lockups, but to the best of my knowledge this conflict remains unresolved.  A shame really.  I debate whether to use LUKS with the Gutsy install based on the problems I'm having now.  

Might have to give Arch a look on this computer at least if nothing fails to work.  I'm kicking myself for wiping Feisty since everything was working.  I just wanted to see what the new talk about Hardy was about.  Now I know but wish I could revert easily.  I screwed myself but Linus/Ubuntu didn't do me any favors either :(

---

### Post by technicalsquash on 2008-05-30
This is affecting me as well. The -16 and previous kernels boot fine, the -17 does not. I also use LUKS and it hangs where I would normally get the login prompt. For now, I've reverted back to -16.

System: acer ferrari 4000
Drive controller:
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller

---

### Post by kevdog on 2008-05-30
Thanks technicalsquash. Only at least for confirming that Im not the only one.  I'll have to wipe the system this weekend, however at least for now will not be putting LUKS back on the system.

---

### Post by technicalsquash on 2008-05-30
I just reverted to the -16 and will continue with that until either a fix is posted or the next revision comes out. Not a huge deal or worth downgrading systems for me, as Hardy fixed several issues I had with Gutsy.

---

