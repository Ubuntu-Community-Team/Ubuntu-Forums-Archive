---
title: "Would this laptop work with Ubuntu?"
date: 2008-08-14
forum: The Cafe
---

### Post by nick09 on 2008-08-14
[http://www.bestbuy.com/site/olspage.jsp?skuId=8913884&type=product&id=1213399970436](http://www.bestbuy.com/site/olspage.jsp?skuId=8913884&type=product&id=1213399970436)

Grabbing a AMD because 1. cheaper and 2. AMD is planning on building a factory in my area!

---

### Post by binbash on 2008-08-15
you may need to recompile the kernel, i do not know if ubuntu's default kernel supports 4gb ram.I have ATI Radeon 2400 HD , i can say ATI drivers suck at linux.It is ok at compiz and that kind of stuff but when it comes to 3d gaming, you can see the garbage  :). Even open source drivers are far better.

It works.Everything will work, the problem is the amount of the work  :)

---

### Post by Lord Xeb on 2008-08-15
Yes... I use an X300 and the graphics performance is poorer than a nvidia at the same level

---

### Post by gn2 on 2008-08-15
> **binbash said:**
> i do not know if ubuntu's default kernel supports 4gb ram.

It does.

If too much RAM was a problem, easier than recompiling would be to remove one memory module, 2gb is plenty.

---

### Post by ssam on 2008-08-15
ATI cards have a much better outlook for the future in linux. ATI/AMD have been releasing all the documentation needed to build open source drivers. They have also partnered with Novel to right open source drivers. NVIDIA cards may give the best performance today (once you have installed the proprietary drivers), but over the next year i expect this to change (hence I have bought a radeon 3650 to replace my nvidia 7300).

To use all the RAM you will need to run the 64bit version of ubuntu (same is true on windows). this is not much different from running 32bit these days. (if you do run 32bit, you just wont be able to see all the RAM, everything will still work)

It does not say which wireless card chipset it is using, so it is impossible to say if it will work.

searching the forum bring up one post [http://ubuntuforums.org/showthread.php?t=884749&highlight=dv5-1004nr](http://ubuntuforums.org/showthread.php?t=884749&highlight=dv5-1004nr)
from the dmesg
```
[   34.991440] wifi%d: unable to attach hardware: 'Hardware revision not supported' (HAL status 13)

```
looks like it has one of the hot new atheros cards. (it is not unknown for manufactures to change chipsets with out telling anyone or changing model numbers). So bad news is that wireless wont work straight away on hardy. good news is that a few weeks ago atheros released an open source driver for these cards ( [http://madwifi.org/wiki/news/20080725/ath9k-atheros-unveils-free-linux-driver-for](http://madwifi.org/wiki/news/20080725/ath9k-atheros-unveils-free-linux-driver-for) ), and it is already included in the 2.6.27 kernel. intrepid will use the 2.6.26 kernel, but i think there is a good chance that this driver will be backported. there are also people getting it to work in hardy [http://ubuntuforums.org/showthread.php?t=874097&highlight=ath9k](http://ubuntuforums.org/showthread.php?t=874097&highlight=ath9k)

---

### Post by grossaffe on 2008-08-15
> **gn2 said:**
> It does.

If too much RAM was a problem, easier than recompiling would be to remove one memory module, 2gb is plenty.

only the 64-bit version supports the 4 gigs, right?

---

### Post by FuturePilot on 2008-08-15
If you have 4GB the 32bit Ubuntu only recognizes about 3.4

---

### Post by gn2 on 2008-08-15
> **grossaffe said:**
> only the 64-bit version supports the 4 gigs, right?

No, the current 32-bit kernel can support 4gb per process up to a total of 64gb.

---

### Post by uberdonkey5 on 2008-08-15
am I wrong, but with a dual processor, won't that mean that if you are running two things at once you have 2GB RAM for each processor? That would be fine in ubuntu wouldn't it? (I mean, things like Vista use the videocard for the graphics anyway, so pretty irrelevant).

---

### Post by nick09 on 2008-08-15
The laptop uses nearly 2GB for graphics. I will be using 64-bit plus you can run 32-bit programs if needed as I have 32-bit java installed on a 64-bit Ubuntu on this PC. Also how will I be able to install the latest kernel if I end up with that wifi card?

I will be installing hardy on it as I want support over a longer period of time.

---

### Post by dragos240 on 2008-08-15
Sounds like ubuntu will run it smoothly

---

### Post by nick09 on 2008-08-15
> **dragos240 said:**
> Sounds like ubuntu will run it smoothly

Ubuntu works smoothly on this old Athlon +3200 with only 878MB of RAM so I have no doubt about the laptop. Should I keep Vista just incase of some games not working in Wine?

---

### Post by original_jamingrit on 2008-08-15
There are ways to run a Vista partition through virtualization (VirtualBox, qemu, etc; ) on Ubuntu, in case WINE isn't perfect.  If you have 4GB of ram, that should be enough to comfortably run Vista in VM.

---

### Post by nick09 on 2008-08-15
> **original_jamingrit said:**
> There are ways to run a Vista partition through virtualization (VirtualBox, qemu, etc; ) on Ubuntu, in case WINE isn't perfect.  If you have 4GB of ram, that should be enough to comfortably run Vista in VM.

How will I be able to do this? I want to build a list of stuff to do when I get the laptop.

---

### Post by bambam123 on 2008-08-23
I actually have this laptop current with ubuntu.

The battery life is a major issue and i have not been able to get around it.  I am actually probably going to have to switch back to Vista :(

Here is a thread I posted about it, looking for help on the issue, since the laptop is so new there was not much help out there

[http://ubuntuforums.org/showthread.php?t=884749&highlight=dv5-1004nr](http://ubuntuforums.org/showthread.php?t=884749&highlight=dv5-1004nr)

---

