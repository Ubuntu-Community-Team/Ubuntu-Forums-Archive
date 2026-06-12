---
title: "VM from recovery discs?"
date: 2008-07-30
forum: Virtualisation
---

### Post by Zeikcied on 2008-07-30
I have a quick question about creating a virtual machine.

I have recovery discs from a previous computer.  The previous computer was a Compaq, as is the current computer.  Both ran Windows XP. (Previous computer is dead.)

Would it be possible to use these recovery discs to install Windows XP in a virtual machine?  The manual says that the discs are "licensed" for a specific PC model, but the discs themselves say they "can only be used with a Compaq PC."  So I assume it will work, but I wanted to see if anyone else knows before I go downloading a VM program.

I should note that these discs were bought from the HP/Compaq Parts store, and were not made within Windows XP.

---

### Post by Shazaam on 2008-07-30
More than likely the disks need to access a hidden "Recovery" partition on the hard drive that is used on most OEM installs and may even tie into the bios. But try it anyway, you never know.

---

### Post by Zeikcied on 2008-07-31
> **Shazaam said:**
> More than likely the disks need to access a hidden "Recovery" partition on the hard drive that is used on most OEM installs and may even tie into the bios. But try it anyway, you never know.
Well, it's five CDs, so I can't help but assume that everything is there.

From my understanding, the discs were meant as a replacement for the recovery partition.

---

### Post by Zeikcied on 2008-07-31
Well I got around to trying, and it didn't work.  Crap.

It complains that this Compaq model isn't the correct one the discs were meant for.  So I guess it either assumes the computer is a Compaq, or VirtualBox allows for some amount of physical hardware to be used.

Anyway...Now I don't have any way to install WinXP in a VM, unless I want to go through the hassle of converting my existing install.  Meh.

---

