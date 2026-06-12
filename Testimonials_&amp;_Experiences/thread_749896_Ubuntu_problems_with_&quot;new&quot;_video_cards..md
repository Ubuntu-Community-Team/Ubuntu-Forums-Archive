---
title: "Ubuntu problems with &quot;new&quot; video cards."
date: 2008-04-08
forum: Testimonials &amp; Experiences
---

### Post by amrclutch1 on 2008-04-08
I have been wondering why the support for new video cards (such as the Nvidia GeForce 8800GT) has been getting worse. Now you may say this is Nvidia's failure to support Linux. This may be true, but everything works flawlessly on openSUSE 10.3. Some of the problems in Feisty for me are somewhat of an annoyance but not too big of a problem. For example, when installing proprietary drivers xorg resets the driver back to vesa after reboot or after killing X. Secondly, the boot screen doesn't show, which isn't really a "problem" but it polishes the system. Hardy Heron beta does the same thing, which I hope will be fixed, I have yet to test the vesa problem on Hardy Heron. Also just to add to balance out the negativity, I like the new theme in Hardy Heron, it looks much cleaner. The "right-click" and menu's left orange bar adds that extra touch, it's nice.

---

### Post by Perfect Storm on 2008-04-09
I'll try if I can answer some of your question :)

> I have been wondering why the support for new video cards (such as the Nvidia GeForce 8800GT) has been getting worse. Now you may say this is Nvidia's failure to support Linux. This may be true, but everything works flawlessly on openSUSE 10.3.

It's always a bit difficult regarding Nvidia drivers as they are closed source (so bugs may go unnoticed, unfixed). I have the oposite experience that the newer cards gets supported quickly. I have a 8800GTX PCI-E 768MB DDR3 card and it's taking both Gutsy (7.10) and now Hardy (8.04) with storm.
Have you checked which version of nvidia driver each distro+version are using?

> Some of the problems in Feisty for me are somewhat of an annoyance but not too big of a problem. For example, when installing proprietary drivers xorg resets the driver back to vesa after reboot or after killing X. Secondly, the boot screen doesn't show, which isn't really a "problem" but it polishes the system. Hardy Heron beta does the same thing, which I hope will be fixed, I have yet to test the vesa problem on Hardy Heron

Did you report the problem(s)? A nice tips is to bug-report, use the "don't expect others will do it" when dealing with such problems. Imagine if it's an unique problem that you only experinces and/or the devs are not aware off.

---

### Post by armandh on 2008-04-09
a computer with a new, off brand, nvidia chipped, video card became surplus when my son the gamer traded up to a computer with a pcie buss.
but when I put ubuntu on it no luck. I swapped to a common video card. everything worked. a few months later I tried it [the video card]  again. and got a pop up message that no open drivers were available and do I want a one anyway.
clicking yes I get it working. WOW

---

### Post by MNICY on 2008-04-10
Well, i know Ubuntu hates my Geforce 5500, but some newer cards seem to be working.
Older ones as well (MX 400 works great! it totaly pwns in the computer it is in, which has 31 mb of ram)

---

### Post by 3rdalbum on 2008-04-11
Ubuntu doesn't seem to be a big fan of my 8600GT, but it works well enough, and the binary driver only occasionally causes all runtime linking to fail, and it's sorta rare that the driver hangs my computer...

---

### Post by Perfect Storm on 2008-04-11
> **3rdalbum said:**
> Ubuntu doesn't seem to be a big fan of my 8600GT, but it works well enough, and the binary driver only occasionally causes all runtime linking to fail, and it's sorta rare that the driver hangs my computer...

Maybe an upgrade of Ubuntu (which have newer drivers, especially for 8XXX series) or install the driver manually from Nvidia.

---

### Post by freebeer on 2008-04-11
The problem may not be just limited to Ubuntu/Linux.  I don't have the card, so I have no first-hand experience.  However, in the Windows world, there's been reported issues with the drivers for that series/family of cards.  It's my impression that they rushed the drivers to get it out for Vista/Aero, but it broke support for legacy applications.

---

### Post by 3rdalbum on 2008-04-12
> **Artificial Intelligence said:**
> Maybe an upgrade of Ubuntu (which have newer drivers, especially for 8XXX series) or install the driver manually from Nvidia.

Heh, I *am* talking about more recent Nvidia drivers downloaded straight from the website. The version that shipped in Gutsy Restricted causes random kernel panics.

Xorg is going through a huge transitional phase at the moment, and Ubuntu has continued to roll in new versions as they come out. I guess it's no surprise that some drivers don't work as well as they used to, for a short while anyway.

---

### Post by Perfect Storm on 2008-04-12
Then it's time to change it where it says feisty at your name ;)
I assumed you was using it.

---

### Post by pcjunkie on 2008-04-20
8800 
8600
8500
8200
All work fine for me. (installed a few Lin boxes lately. A pc at work has an 8800 and it runs sweet. (Using 7.10. 8.04 it freaked out and reported a display of sub 600. it was 1689x1050)

9600 and 9800 as far as I know don't have a driver yet., (you can thank Nvidia and gigabyte for that)

---

### Post by dark_harmonics on 2008-04-21
The NVIIDIA 8600 in my mac pro works with the proprietary drivers, but sucks at 2d rendering. This is not Ubuntu specific because i see posters in other distros seeing the same problem. NVIDIA needs to fix it...

---

