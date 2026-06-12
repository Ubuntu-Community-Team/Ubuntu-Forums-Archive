---
title: "After all these years"
date: 2008-11-26
forum: Testimonials &amp; Experiences
---

### Post by lauragee on 2008-11-26
After all the years that i have tried to install linux i still have never succeeded. i'm writing to the forums in the hopes that i may at some point succeed.
Ever since way back in version 6 and in all different flavors, i have tried to install with a dual boot configuration and i always come up against the same problem, i'm never able to see an entry in a dual boot menu where i can launch linux.
i'm not even sure if the grub menu is the same thing as the  dual boot menu that i have seen for dual booting of various versions of Windows !!....is it?
At this point i'm so confused with all the advise re; drive configurations and ppl talking about sda and hd0, hd1 and all the other stuff that i have almost given up on ever using linux. i'm so sick of windows it's unbelievable.
i have tried many diff configurations of installing both OS, all without success.
i have installed Xp first then linux (same drive, diff partitions). Linux first then Xp (same drive diff partitions).
Same as both above but on completely different drives.
i have also done ALL of the above using Linux and vista.
In fact i can't think of any configuration of the OS that i have't tried. All the above were fresh installs.
i have read all the forums over the last few years in the hopes that the advise here would change or be updated but it hasn't and it is all JUST as confusing to me as it ever was.
i really am hoping someone can help me with something i can understand. i don't THINK i'm so impossibly stupid in not understanding it all but i really have followed all the advice and it's because non of it has ever succeeded is the reason why i feel it is me, not installing properly that is the problem, hence my confusion when non of it works.
i dunno if any of this has made any sense but here is hoping some friendly soul will answer with some advice.

---

### Post by handydan918 on 2008-11-26
This really shouldn't be that hard. If you have been trying to install Linux for that long, I would suggest that you look for a LUG (Linux Users Group) in your area, and ask them to help. It's what they do. It's who they are. They really can't even help themselves....

---

### Post by nhasian on 2008-11-26
linux has come a long way in the past few years.  i finally switched over myself after checking back in with redhat every couple of years.  Very easy to use now.

Shouldnt matter if your operating systems are on the same drive or not.  If you have Windows installed first, then install Ubuntu 8.10 from the liveCD onto a different drive/partition then you will have a menu to choose which OS to boot when you turn the computer on.  Its pretty straight forward.

---

### Post by yanceypd on 2008-11-27
I'm sure because I'm new at Linux too. I was able to install ubuntu to a clean slave drive from Windos operating System.  While running windows I use an Ubuntu disk and installed it to the slave drive.  During the boot up process look for some lines that pop up asking what operating system you want to run.  I may have just been lucky but that worked for me.  Runing Vista and Ubuntu 8.04 now upgraded to 8.10

---

### Post by Iendicis on 2008-11-27
You could always try to install Ubuntu under Windows, too. Just put the CD in under Windows and install.

---

### Post by waspbr on 2008-11-27
For a new use the installation process may be a very scary place, I remember my first few attempts, everything was very new and I really did not know 100% what I was doing.

However, some videos in youtube were extremely helpful. 

[http://www.youtube.com/watch?v=JBfl3oViny8]("http://www.youtube.com/watch?v=JBfl3oViny8")

this one for instance walks you through the whole process, it is made for gutsy (7.10) but it should be pretty much the same process for 8.4 and 8.10.

Good luck and don't hesitate to post if you need any help

---

### Post by stalkingwolf on 2008-11-27
OK first lets make this easy for all who are trying to help.

What are the specs of the system you are working with?  Laptop or desktop?
Processor and ram ? do you know what video card or chip?

From what you say you have more than one HDD available.  Have you tried
installing to a drive with out windows in the loop?  When I am having problems I always revert to the KISS method.

If the independant install works then move on.  But at every step as Reagan
told Gorby "trust but verify".

You might also want to download a copy of the Supergrub live CD.  I have never had to use it.  But I understand it is a lifesaver at times.

I have also found that what you use to format and partition can make a difference.

---

### Post by armandh on 2008-11-27
yes the grub menu displayed [just after the boot from CD fails]
is the selection. use the up & down arrows and enter. top of the list is the default time out. [a non standard usb key board may not work at this point or std one if support not enabled in the bios] try the regular round plug type if this is a problem.

if you are trying to dual boot with vista use the vista hard drive partition utility to reduce the size of the vista partition and when installing Ubuntu select largest empty space.


this all assumes there is not an exotic HDD encryption or compression at work.

---

### Post by lauragee on 2008-11-27
> **stalkingwolf said:**
> OK first lets make this easy for all who are trying to help.

What are the specs of the system you are working with?  Laptop or desktop?
Processor and ram ? do you know what video card or chip?

From what you say you have more than one HDD available.  Have you tried
installing to a drive with out windows in the loop?  When I am having problems I always revert to the KISS method.

If the independant install works then move on.  But at every step as Reagan
told Gorby "trust but verify".

You might also want to download a copy of the Supergrub live CD.  I have never had to use it.  But I understand it is a lifesaver at times.

I have also found that what you use to format and partition can make a difference.

i took your advice and DL Super grub and used it. i get the exact same thing. It SEEMS to successfully complete but when i reboot there is still no option in my boot menu to boot Ubuntu.
i have even tried using EasyBCD to create a boot option and altho i succeed in creating Ubuntu in my boot menu, when i try to boot Linux all i get is a flashing cursor beside the the GRUP prompt, i.e  GRUB>....with some fail text above it.
This is the problem i have come up against EVERY time i have tried to install linux, no matter what configuration or in what order i try to install it.
It really is very frustrating.

---

### Post by handydan918 on 2008-11-27
we need some errors. 
Boot the live cd, open a terminal and do ```
sudo fdisk -l
```

Let's see what you got.

---

### Post by lauragee on 2008-11-27
> **handydan918 said:**
> we need some errors. 
Boot the live cd, open a terminal and do ```
sudo fdisk -l
```

Let's see what you got.

Below is what i have as you requested and as you can see i habe Ubuntu dedicated to the 160 gig disk.

ubuntu@ubuntu:~$ sudo fdisk -l



Disk /dev/sda: 80.0 GB, 80026361856 byte
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x410e410e



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1        3356    26957038+   7  HPFS/NTFS
/dev/sda2            3357        6543    25599577+   7  HPFS/NTFS
/dev/sda3            6544        9729    25591545    f  W95 Ext'd (LBA)
/dev/sda5            6544        9729    25591513+   7  HPFS/NTFS



Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ad77f

   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1               1       18662   149902483+  83  Linux
/dev/sdb2           18663       19457     6385837+   5  Extended
/dev/sdb5           18663       19457     6385806   82  Linux swap / Solaris


Disk /dev/sdc: 320.0 GB, 320072933376 bytes
102 heads, 51 sectors/track, 120173 cylinders
Units = cylinders of 5202 * 512 = 2663424 bytes
Disk identifier: 0x7573980c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60070   156242038+   7  HPFS/NTFS
/dev/sdc2           60070      120173   156327897    f  W95 Ext'd (LBA)
/dev/sdc5           60071      120173   156327871+   7  HPFS/NTFS

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
37 heads, 15 sectors/track, 1126382 cylinders
Units = cylinders of 555 * 512 = 284160 bytes

Disk identifier: 0xd96c74a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1      369487   102532611    7  HPFS/NTFS
/dev/sdd2          369487     1126379   210037482    f  W95 Ext'd (LBA)
/dev/sdd5          369487      738974   102532611    7  HPFS/NTFS
/dev/sdd6          738974     1126379   107504856    7  HPFS/NTFS

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x880b0ef3

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1       15197   122069871    7  HPFS/NTFS
/dev/sde2           15198       30401   122126130    f  W95 Ext'd (LBA)
/dev/sde5           15198       30401   122126098+   7  HPFS/NTFS

Disk /dev/sdf: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x0c320c32

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1        7266    58364113+   7  HPFS/NTFS
/dev/sdf2            7267       14592    58846095    f  W95 Ext'd (LBA)
/dev/sdf5            7267       14592    58846063+   7  HPFS/NTFS


Disk /dev/sdh: 4102 MB, 4102889984 bytes
255 heads, 63 sectors/track, 498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95fe95fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1         497     3992135+   b  W95 FAT32

ubuntu@ubuntu:~$ 
thanks

---

### Post by m_l17 on 2008-11-27
Ubuntu Wiki has a good guide:

[https://help.ubuntu.com/community/GraphicalInstall]("https://help.ubuntu.com/community/GraphicalInstall")

---

### Post by lauragee on 2008-11-27
> **m_l17 said:**
> Ubuntu Wiki has a good guide:

[https://help.ubuntu.com/community/GraphicalInstall]("https://help.ubuntu.com/community/GraphicalInstall")

thank you for the link and yes, it is a great overview of the install but my problem is that no matter how or where i install ubuntu i never see it in my boot menu, hence i am unable to load it after i reboot. i have tried every configuration i can think of to install it including auto install, making a partition, using the largest free space as well as installing on a dedicated hard drive and in every case i get the same result.

After writing the above i actually went and reformatted the drive i want dedicated to Linux and did a fresh ubuntu install. The option to boot Ubuntu again wasn't there.
i even tried to add the boot entry using EasyBCD. The entry was made but when i choose it all i get is a screen with the GRUB prompt. i.e. ...GRUP> with a flashing cursor

---

### Post by m_l17 on 2008-11-27
Take a look at this to boot from cd:

[https://help.ubuntu.com/community/BootFromCD]("https://help.ubuntu.com/community/BootFromCD")

---

### Post by lauragee on 2008-11-27
> **m_l17 said:**
> Take a look at this to boot from cd:

[https://help.ubuntu.com/community/BootFromCD]("https://help.ubuntu.com/community/BootFromCD")
My problem isn't that i can't boot from the live Cd, it is that i cannot boot into ubuntu from my system boot menu  (no option in the boot menu for linux) after i have installed ubuntu on my hard drive.

---

### Post by psusi on 2008-11-27
My you have a lot of disks, with a lot of partitions.  It sounds like you are saying you still boot directly into windows after installing Ubuntu, which means GRUB isn't being loaded, probably because it isn't installed on the right disk.  Grub will be installed on your sda disk by default.  If that is not the disk that the bios is set to boot from, then that is the cause of your problem.  Either change the bios to boot from that disk, or reinstall grub to the disk the bios does boot from.

---

### Post by 3rdalbum on 2008-11-28
My god, what on earth is happening on your computer? That is a seriously HUGE number of hard disks and partitions that you have, or at least that Linux thinks you have. I'd find out where and when your local LUG is meeting next, and see if you can get their help with installing Ubuntu or some other form of Linux on it.

---

### Post by m_l17 on 2008-11-28
> **lauragee said:**
> My problem isn't that i can't boot from the live Cd, it is that i cannot boot into ubuntu from my system boot menu  (no option in the boot menu for linux) after i have installed ubuntu on my hard drive.

I see, try selecting hard drive that Ubuntu is installed from the bios and boot that way. Temporary fix until you get some local help.

---

