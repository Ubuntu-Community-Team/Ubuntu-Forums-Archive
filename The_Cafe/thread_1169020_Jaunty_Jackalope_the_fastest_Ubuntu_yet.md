---
title: "Jaunty Jackalope the fastest Ubuntu yet?"
date: 2009-05-24
forum: The Cafe
---

### Post by hal8000 on 2009-05-24
Finally got Jaunty installed, the Desktop CD worked fine in Live mode but failed to install. Downloaded the alternate install cd for 32bit x86 and now have a working installation.

Boot speed is quite impressive. Installed bootchart and... its 21 seconds !!



I havent even yet removed startup and desktop services that I dont need.

System is Intel Pentium 4 2.8 GHz (single core)
1G RAM
Nvidia 7600GT card

This is the fastest Ubuntu yet for me, what boot speed is everyone else seeing?

---

### Post by lovinglinux on 2009-05-24
If you are just asking about boot time, then yes.

If you are talking about data transfer, then yes. But this would be a consequence of ext4.

If you are talking also about overall performance, then no. I still have issues with it. I prefer to have 5 minutes boot time and a better overall performance.

BTW, my boot time is 24 seconds. I have a P4 3.06 Ghz HT, 2Gb DDR2 RAM and nVidia 7300 GT.

---

### Post by Dark Aspect on 2009-05-24
I vote Ubuntu 7.04, but Jaunty Jackalope is very fast and its something that I hope stays around even though I have my doubts. I am happy with it for now but once Ubuntu starts slowing down again I'll be done with it; there are too many other, faster Linux distros than Ubuntu. I was planing on going with Mint Linux for good but when I tested Ubuntu 9.04 I was impressed, if I do abandon Ubuntu as an OS, I'll probably still be a (small) part of the forums.

---

### Post by cl333r on 2009-05-24
-Intel users should not be too happy.
-Boot time is better.
-ext4 is snappier for file operations
-overall Gtk responsiveness seems a bit faster
-kernel 2.6.28 is slow for I/O and sqlite operations (think of Firefox), both of which are solved in the 2.6.29/30 kernel which has (will have) a better CFQ I/O scheduler:
[http://www.h-online.com/open/Kernel-Log-What-s-coming-in-2-6-30-Storage-RAID-improvements-optimised-CFQ-Scheduler-SAS-drivers--/news/113302](http://www.h-online.com/open/Kernel-Log-What-s-coming-in-2-6-30-Storage-RAID-improvements-optimised-CFQ-Scheduler-SAS-drivers--/news/113302)

For nvidia users like me, the best thing happened: almost no nvidia bugs so far, including Java related and even VDPAU support, that's what makes Jaunty even greater (for me)!

---

### Post by ghindo on 2009-05-24
I always like to think that the best Ubuntu is yet to come - improvements are always being made on all fronts, improving the stack as a whole :)> **lovinglinux said:**
> If you are talking also about overall performance, then no. I still have issues with it. I prefer to have 5 minutes boot time and a better overall performance.Define "overall performance."

---

### Post by pwnst*r on 2009-05-24
recurring ->

---

### Post by lovinglinux on 2009-05-24
> **ghindo said:**
> I always like to think that the best Ubuntu is yet to come - improvements are always being made on all fronts, improving the stack as a whole :)Define "overall performance."

Do I need?

Like for example too much CPU being used for regular tasks, flash stuttering like hell, windows operations delay, applications responsiveness. That kind of stuff.

---

### Post by ghindo on 2009-05-24
> **lovinglinux said:**
> Do I need?

Like for example too much CPU being used for regular tasks, flash stuttering like hell, windows operations delay, applications responsiveness. That kind of stuff.I haven't experienced any of those issues.  The only regression in performance I have experienced with 9.04 has been the Intel chipset business.  And even if I *had* experienced those issues, I hardly think that Canonical has any control over Flash performance.

---

### Post by BeachBum on 2009-05-24
> **cl333r said:**
> -Intel users should not be too happy.


I have an x3100 (GM965), and video was noticeably slower than previous releases, but the latest kernel (2.6.30rc7) from the ubuntu kernel ppa is blazingly fast! 

With the latest PPA kernel, 9.04 is the fastest on all fronts for me.

Now if only I could decrease the login speed, and get to a full gnome desktop in 30s :p

---

### Post by lovinglinux on 2009-05-24
> **BeachBum said:**
> I have an x3100 (GM965), and video was noticeably slower than previous releases, but the latest kernel (2.6.30rc7) from the ubuntu kernel ppa is blazingly fast! 

With the latest PPA kernel, 9.04 is the fastest on all fronts for me.

Now if only I could decrease the login speed, and get to a full gnome desktop in 30s :p

This kernel from the PPA is official? Would it be incorporated into Jaunty in the future? If I use it, can I roll back to the regular official kernel if something goes wrong? What's the address of this PPA?

---

### Post by logos34 on 2009-05-24
> **lovinglinux said:**
> If I use it, can I roll back to the regular official kernel if something goes wrong?

yes, you should still be able to select your older kernel from the grub menu

---

### Post by lovinglinux on 2009-05-24
> **logos34 said:**
> yes, you should still be able to select your older kernel from the grub menu

Thanks. But if I don't want to use it anymore and remove the PPA from sources list, then my kernel will be updated when a new version is released through the main repository?

---

### Post by logos34 on 2009-05-25
> **lovinglinux said:**
> Thanks. But if I don't want to use it anymore and remove the PPA from sources list, then my kernel will be updated when a new version is released through the main repository?

right, you'll get the official kernel updates through main

---

### Post by ghindo on 2009-05-25
> **BeachBum said:**
> I have an x3100 (GM965), and video was noticeably slower than previous releases, but the latest kernel (2.6.30rc7) from the ubuntu kernel ppa is blazingly fast! 

With the latest PPA kernel, 9.04 is the fastest on all fronts for me.

Now if only I could decrease the login speed, and get to a full gnome desktop in 30s :pInteresting.  Was the only modification you made the new kernel?  Or did you modify other things as well?

How do you install the new kernel, anyway?

---

### Post by andrewabc on 2009-05-25
It looks like Jaunty is the fastest version for me.
Currently bootchart says 19 seconds.

I previously made several posts in "attach bootchart" thread.
Intrepid was between 24 and 26 seconds.
Hardy was 25 seconds.
Gutsy was 22 seconds.

The reason for speed increase probably has to do with me using ext4 and 64 bit. previously it was ext3 and 32 bit.

---

