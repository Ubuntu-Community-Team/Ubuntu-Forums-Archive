---
title: "Stopped Using Lucid (for now...)"
date: 2010-05-18
forum: Testimonials &amp; Experiences
---

### Post by Blackbird_13 on 2010-05-18
I have just gone back to Jaunty after a pretty awful try out of Lucid.   

 I have 2 PCs: an Inspiron 545 and a XPS 1730. I installed onto sdb of the desktop (vista on sda – don't ask!) using *ubuntu-10.04-desktop-i386.iso* on a USB. I also tried a live session using the USB on my laptop.  Problems so far:  
 
 **Problem 1 - partitioning  **
 
 As part of the installation process I chose to do a manual partitioning. The re-partitioning left 1mb free space between a number of my partitions (sdb1, sdb4, sdb6, sdb7, sdb8 and sdb9) . sfdisk as follows.  
 
```
Disk /dev/sdb: 60801 cylinders, 255 heads, 63 sectors/track  
 Warning: extended partition does not start at a cylinder boundary.  
 DOS and Linux will interpret the contents differently.  
 Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0  
  
    Device Boot Start     End   #cyls    #blocks   Id  System  
 /dev/sdb1          0+     12-     12-     96256   83  Linux  
 /dev/sdb2         12+   2443-   2432-  19530752   83  Linux  
 /dev/sdb3       2443+  14601-  12158-  97655808   83  Linux  
 /dev/sdb4      14601+  28351   13751- 110452576+   5  Extended  
 /dev/sdb5      14601+  16789-   2189-  17576960   83  Linux  
 /dev/sdb6      16789+  17032-    243-   1951744   82  Linux swap / Solaris  
 /dev/sdb7      17032+  17640-    608-   4881408   83  Linux  
 /dev/sdb8      17640+  26758-   9119-  73241600   83  Linux  
 /dev/sdb9      26759+  26821      63-    506016   83  Linux  
 /dev/sdb10     26822+  28351    1530-  12289693+  83  Linux  

``` Hardly a major problem but annoying all the same. This hasn't happened with previous installations of Jaunty - something to do with rounding to cylinders? I couldn't see any box to tick/untick in order to avoid the problem.  I ended up doing 2 installations of Lucid and it happened both times. Gparted won't allow me to utilise the free space by expanding the preceding partition(s).  
 
**Problem 2 - ATI/AMD proprietary FGLRX driver  **
 
 I have a Radeon HD4350. Activating the FGLRX driver I re-booted into a black screen, so I had to reboot into recovery mode and remove the driver. To be fair this is a problem I have in Jaunty as well. I cannot get my Dell 17inch monitor to be recognised by the system.  
 
 **Problem 3 - failure to restart/shutdown  **
 
 There are two separate problems:
 
(a) Clicking on the shutdown icon (top panel rhs) did nothing. It did not generate a  pull down menu to choose restart/logout/shut down. I had to sudo reboot in a terminal. 

 (b) At other times I can generate the pull down menu but clicking on shut down or restart does nothing and I have to resort to the terminal to close down.

The problems don't happen all the time, but there seems to be no rhyme or reason as to when they do.  
 
 **Problem 4 - Power Manager is not responding**
 
 At the initial log-in screen I got an error message about a program still running and "Power Manager not responding". The system freezes unless I let the dialogue box disappear in c5 seconds time. I can then log in as normal. Other users seem to have similar problem.
 
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/563862](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/563862)
 
The problem seemed to go away when I edited grub.cfg and removed quiet splash and added nomodset to the following:
 
 ```
linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=1176f065-ef2c-4a29-8dea-7ba54a305d6f ro   nomodeset
``` [B]
Problem 5  [/B]
 
 Using the Lucid USB I tried a live boot on my laptop ((NVIDIA accelerated graphics driver version 180). It booted into a desktop ok, but the PC became noisy (like a jet engine) so I shut down. I also noticed that my desktop was making a noise, albeit not as loud. On researching I came across these worrying threads.  
 
 [https://lists.ubuntu.com/archives/ubuntu-devel/2010-March/030380.html](https://lists.ubuntu.com/archives/ubuntu-devel/2010-March/030380.html)
 [http://ubuntuforums.org/archive/index.php/t-1458089.html](http://ubuntuforums.org/archive/index.php/t-1458089.html)
 
 Problems 1 to 4 I could live with and/or do more research and resolve. But problem 5 is a no no, so I ended up re-installing Jaunty.  
 
 **Current Set-up  **
 
 Rather than remove Lucid, I did a bit more research and have ended up with a dedicated grub2 partition independent of any operating system.  I found this link very informative:
 
 [http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/](http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/)
 
I knew nothing about Grub2 before I started so it was a pretty steep learning curve. I then re-installed Jaunty on a separate partition. I also did something I've been meaning to do for ages which is move all my user files to a separate data partition. I did a bit more research and learnt how to create symbolic links in my Lucid and Jaunty home directories. Along the way I also changed a user account name retaining the UID and GID. I had never done anything like this before and found it all rather fun (how sad am I) and very satisfying when it worked.  
 
 **Summary**  
 
  I only started using Ubuntu last Autumn and I loved it straight away. I've made mistakes along the way - but that's the way to learn and I have installed Jaunty on my dad's and brothers PCs.  
 
 I felt really deflated when I had the Lucid problems. Problems 3 and 4 were really annoying and problem 5 PC destroying. My confidence in Ubuntu was badly shaken. 

 However, without the problems I would never have gone through a wonderful learning experience so, with the benefit of hindsight, I feel pretty positive about the whole experience. I'll try Lucid in a couple of months time to see whether my problems have been resolved.

---

### Post by Tamlynmac on 2010-05-18
> Blackbird_13

Sorry, you had problems with the newest release. Hopefully, when you try it again in a few months, you'll have more success.

Good Luck

---

### Post by Ms_Angel_D on 2010-05-19
Blackbird_13, thanks for sharing your experience. Feel free to utilize the support sections of the forum. If you indeed decide your path lies elsewhere feel free to submit bug reports, so that some of the issues your experiencing are noted and hopefully receive some attention.

Angel

---

### Post by uRock on 2010-05-19
Sounds like something as simple as a new ISO image could fix some of your issues. Thanx for sharing, maybe you can give it a chance again in a month or two after the rest of the kinks are worked out.

Cheers,
uRock

---

### Post by Blackbird_13 on 2010-05-19
Many thanks for your replies. If I still have problems when I give it another go I shall certainly take the opportunity to pick the brains of forum members.

Best wishes.

---

