---
title: "[SOLVED] Grub hard drive designations"
date: 2009-01-06
forum: Ubuntu Brainstorm
---

### Post by 73ckn797 on 2009-01-06
I posted a similar query in another post several months ago but felt that it is something that needs to be fixed and could save people a lot of problems.

What can be done to correct hard drive order when grub is created?

When I boot from a live CD the physical/BIOS hard drive order is never consistent with how Ubuntu/Linux reads it or how grub configures it. This results in the grub menu rarely being correct and creating error 17 or 22 on start-up. It also has prevented the other OS from booting.

Example: physical/BIOS drive order is 250Gib in IDE Master; 160Gib drive on SATA 1; and 160Gib drive on SATA2. The assumption is that #1 is hd0, #2 is hd1 & #3 is hd2. That seems to be a logical assumption.

OS installations are Windows XP on 1st drive (hd0,0) (sda1) and Ubuntu on 2nd (hd1,0)-(sdb1). Live CD and grub always assign (hd0,0) to either (hd1,0)-(sdb1) or (hd2,0)-(sdc1). It then writes Ubuntu as (hd0,0)-(sda1). This creates an un-bootable system. I have had to almost always edit the menu.lst to correct this to the actual physical drive order to make things work. Even Super Grub Disk (SGD) makes the same error. There have been several times that I had to edit grub to a different designation than what I mention here. The only way that I have been able to figure it out was using the grub menu editing option.

I am constantly seeing posts from beginners that are having to deal with this issue. Can this be something that can be remedied via programming? Can't the programming read the physical BIOS order and work from that? It seems to want to read drive order based upon its own desires at any given time. (I seem to ascribe to Ubuntu a life of it's own) There have been one or two times that it got it right but that has been the exception.

It can be a real turn-off for the new user to have to deal with what they may see as a system broken by the installtion of Ubuntu. This may be a problem generally with Linux but I have only used Ubuntu.

My first installation did not have this problem but I am one to tinker and try things out. That is how I discovered the issue and also how I figured this all out. If this is just the way things are then Ubuntu will not be a viable alternatuve for many. I realize that it will never be for everyone. It has generally "just worked" for me.

---

### Post by smartboyathome on 2009-01-08
This is solved in Grub2. They have Grub generate a "device.map" which can be changed to reflect which hard drive is which.

---

### Post by 73ckn797 on 2009-01-08
> **smartboyathome said:**
> This is solved in Grub2. They have Grub generate a "device.map" which can be changed to reflect which hard drive is which.


Is that going to be in a later (Jaunty?) Ubuntu?

---

### Post by smartboyathome on 2009-01-08
> **73ckn797 said:**
> Is that going to be in a later (Jaunty?) Ubuntu?

No, as it is not considered 'stable' yet. Nor is it really backportable (Grub changed too much between legacy and 2). I run Grub2 on Arch Linux, though, and have no problems with it. Give it a try (perhaps in a VM, of course, so that you don't mess up your install ;)) to see if you like it. :)

---

### Post by 73ckn797 on 2009-01-11
Considered solved.

Since Grub2 is not ready for implementation into Ubuntu, I will not take any chances nor waste the time on it until it is ready.

---

### Post by BLTicklemonster on 2009-01-22
Jeez, you'd think there was a way to determine which hd was which. I have 4, so it ought to be hd0 through hd3, but I can't get grub to work with one I know is in there no matter what entry I use. I know it's either hd1,1 or hd3,1 because hd0,1 and hd2,1 have ubuntu loaded on both of them, and the other hard drive is storage only. The one in question has two partitions, the first, hd*,0 would not be the operating system, but hd*1, the second partition is the one with the operating system. I edit menu.lst so reflect either hd1,1 or hd3,1, yet each time I try to select the drive at the grub menu, it says that's not a partition. Dang.

And I don't really want to go having to installing anything on a disk to use it...

Oh well.

---

