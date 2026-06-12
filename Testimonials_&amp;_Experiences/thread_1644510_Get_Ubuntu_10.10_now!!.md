---
title: "Get Ubuntu 10.10 now!!"
date: 2010-12-13
forum: Testimonials &amp; Experiences
---

### Post by Kramer2010 on 2010-12-13
Hi, I'm running Ubuntu 10.10 on a packard bell easynoteTJ68 and its f******g brilliant!  no problems at all apart from my lack of experience with linux OS.  Runs very smoothly and boots in 30secs, beat that bill.  

Installed with wubi and dual booting with Win 7 premium 64bit
Pentium(R) Dual-Core CPU   T4400 @ 2.20GHz
Ram 4Gb
320 Gb HD
Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)

---

### Post by ajgreeny on 2010-12-13
And if you're brave enough to repartition your hard drive and do the dual boot properly, you would find it to be even better, I expect!

Wubi is really only meant to test out the OS to see if it works on your hardware and if you like it enough to keep it.  Having found that it does, and you do, I suggest you investigate partitioning your hard drive and putting ubuntu on there properly, in its own partitions.

Unfortunately Win7 has a nasty habit of installing using all of the four primary partitions that can be made on a hard disk, and therefore it may be necessary to delete one of the existing partitions and/or resize others to make room for ubuntu.

So if you decide to look into this further, ask here again and show us the output of ```
sudo fdisk -l
``` in terminal, and/or a screenshot of gparted running and showing all your partitions.  The screenshot can be very helpful as it shows the relative sizes and arrangement on disk of partitions.

---

### Post by Kramer2010 on 2010-12-14
> **ajgreeny said:**
> And if you're brave enough to repartition your hard drive and do the dual boot properly, you would find it to be even better, I expect!

Wubi is really only meant to test out the OS to see if it works on your hardware and if you like it enough to keep it.  Having found that it does, and you do, I suggest you investigate partitioning your hard drive and putting ubuntu on there properly, in its own partitions.

Unfortunately Win7 has a nasty habit of installing using all of the four primary partitions that can be made on a hard disk, and therefore it may be necessary to delete one of the existing partitions and/or resize others to make room for ubuntu.

So if you decide to look into this further, ask here again and show us the output of ```
sudo fdisk -l
``` in terminal, and/or a screenshot of gparted running and showing all your partitions.  The screenshot can be very helpful as it shows the relative sizes and arrangement on disk of partitions.

I agree that I am taking the easy way out as far as the installation goes, but what benefits would I see if I went for repartitioning and correct dual boot install? (which I originally attempted, however no option for auto partition and dual boot offered at install)

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x43764375

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1658    13312000   27  Unknown
/dev/sda2   *        1658        1671      102400    7  HPFS/NTFS
/dev/sda3            1671       38914   299154776    7  HPFS/NTFS

---

### Post by ajgreeny on 2010-12-14
Well, I'm not a windows user so can not comment on the versions of windows after XP, but the main problem I see in wubi, is that it is always going to be totally dependent on a good running windows OS.  If something goes wrong with the windows install you have lost both that and your ubuntu.

I would have a good look at [Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome")and see if you can follow that to get a real dual boot, that does not still need windows.

---

### Post by AlanR8 on 2010-12-14
Unlike me, who usually goes to the cutting leading bleeding edge as soon as its available, this time I've stuck with 10.04 on all my machines! 

I tried 10.10 just after release time but found my Interweb speeds unacceptable on this Compaq Mini and to a lesser extent Sony Vaio.

Put this down to driver issues and a reversion to 10.04 just sorted all the issues out! Fortunately with Gmail and Dropbox, these days I store almost nothing on my HDs so rebuilding is quick and easy.

---

### Post by johntaylor1887 on 2010-12-15
> **ajgreeny said:**
> 

Wubi is really only meant to test out the OS to see if it works on your hardware and if you like it enough to keep it.  Having found that it does, and you do, I suggest you investigate partitioning your hard drive and putting ubuntu on there properly, in its own partitions.



I agree with this. Wubi should not be used as a long term solution. Right now for you, Ubuntu is installed inside of windows. Each operating system deserves it's own partition independent of each other. You will not find any serious linux people using wubi. <shudders>

---

### Post by Kramer2010 on 2010-12-15
> **johntaylor1887 said:**
> I agree with this. Wubi should not be used as a long term solution. Right now for you, Ubuntu is installed inside of windows. Each operating system deserves it's own partition independent of each other. You will not find any serious linux people using wubi. <shudders>

I know, I know, I should do the right thing, but its all going so well!  Give me some more time, need more time, looking for idiot proof step by step graphical instructions. 

 I've always tended to throw written instructions for anything technical (pc's, tv's) in the bin and grudgingly looked thru the 'quick start guides.  Bit more hassle with OS's tho and if it aint broke (yet), I sometimes try not to fix it, so the above is putting temptation in my way...  ;)

---

### Post by mick222 on 2010-12-15
> I know, I know, I should do the right thing, but its all going so well! Give me some more time, need more time, looking for idiot proof step by step graphical instructions. 
 Take your time It's pretty easy to set up dual boot Ubuntu will resize and set up partitions for you check out this link [http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)

---

### Post by Kramer2010 on 2010-12-15
> **mick222 said:**
> Take your time It's pretty easy to set up dual boot Ubuntu will resize and set up partitions for you check out this link [http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)

[FONT="Arial"]Well I finally did it, everything seems ok so far, but... This is what I did

1) In windows I shrank my windows partition (eek)
2) My new partition E is approx 130gig (have 150gig for win 7 in C/)
3) At installation I chose "install alongside window"
4) I dragged slider to left to get max storage and continued install.

After install Ubuntu disk usage analyzer shows 2.9GB of 119.9GB used.

However in windows 7 Drive E is shown as having a total of 3GB... did I screw up?[/FONT]

---

### Post by Kramer2010 on 2010-12-15
> **Kramer2010 said:**
> [FONT="Arial"]Well I finally did it, everything seems ok so far, but... This is what I did

1) In windows I shrank my windows partition (eek)
2) My new partition E is approx 130gig (have 150gig for win 7 in C/)
3) At installation I chose "install alongside window"
4) I dragged slider to left to get max storage and continued install.

After install Ubuntu disk usage analyzer shows 2.9GB of 119.9GB used.

However in windows 7 Drive E is shown as having a total of 3GB... did I screw up?[/FONT]

Just remembered heres my sudo fdisk-1

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x43764375

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1658    13312000   27  Unknown
/dev/sda2   *        1658        1671      102400    7  HPFS/NTFS
/dev/sda3            1671       21939   162808152    7  HPFS/NTFS
/dev/sda4           21940       38914   136345601    f  W95 Ext'd (LBA)
/dev/sda5           21940       22331     3145988    7  HPFS/NTFS
/dev/sda6           22331       38235   127746048   83  Linux
/dev/sda7           38235       38914     5451776   82  Linux swap / Solaris

Also...

[http://farm6.static.flickr.com/5202/5263856304_229cc32856_b.jpg](http://farm6.static.flickr.com/5202/5263856304_229cc32856_b.jpg)

---

### Post by johntaylor1887 on 2010-12-15
> **Kramer2010 said:**
> [SIZE="3"][FONT="Arial"]

However in windows 7 Drive E is shown as having a total of 3GB... did I screw up?[/FONT][/SIZE]

Win7 needs at least 20gb of space to run, so that 3gb partition is probably your restore partition. Have fun!

---

### Post by Kramer2010 on 2010-12-15
> **johntaylor1887 said:**
> Win7 needs at least 20gb of space to run, so that 3gb partition is probably your restore partition. Have fun!

Sorry what I meant to say was that it is my new partition (E) for unbuntu

---

### Post by Old_Grey_Wolf on 2010-12-15
That all looks good.

I'm actually surprised that Windows 7 is trying to label it as E:. Vista doesn't label it. It only shows that a partition exists.

Edit: I looked at the picture you attached. The 121.83 GB partition is Ubuntu and the 5.20 GB is your Linux swap partition. I don't know what the 3 GB E partition is. Did you give the WUBI install its own NTFS formatted partition?

> **Kramer2010 said:**
> Just remembered heres my sudo fdisk-1

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x43764375

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1658    13312000   27  Unknown
/dev/sda2   *        1658        1671      102400    7  HPFS/NTFS
/dev/sda3            1671       21939   162808152    7  HPFS/NTFS
/dev/sda4           21940       38914   136345601    f  W95 Ext'd (LBA)
/dev/sda5           21940       22331     3145988    7  HPFS/NTFS
/dev/sda6           22331       38235   127746048   83  Linux
/dev/sda7           38235       38914     5451776   82  Linux swap / Solaris

Also...

[http://farm6.static.flickr.com/5202/5263856304_229cc32856_b.jpg](http://farm6.static.flickr.com/5202/5263856304_229cc32856_b.jpg)

---

