---
title: "Installing on Lenovo ThinkServer RD440 with Raid 1+0 (4x2TB): Issues on Partitioning"
date: 2015-01-02
forum: Server Platforms
---

### Post by office.partsch on 2015-01-02
We bought a new Lenovo ThinkServer RD440. I configured the Raid Controller using Lenovos EasyStartup DVD to a Raid Level 1+0 using four 2 TB Disks. Then I downloaded ubuntu-14.04.1-server-amd64.iso and copied it onto an USB Stick. The ThinkServer successfully booted from USB and started the Ubuntu Installation; which works fine until partitioning:

While detecting disks it asks to "Activate MDADM containers (Intel/DDF RAID)" and immediately after "Activate Serial ATA RAID devices". I select yes for on both queries and it takes me to the partition menu. There I'll get the options "Guided Partitioning", "Configure iSCSI volumes" (which I persume can be ignored) , "SCSI9 (0,0,0) (sde) - 8.2 GB General UDisk" (The USB Stick I'm installing from), "Undo changes to partitions", "Finish partitioning and write changes to disk". I cannot select my disk array to partition, and by just pressing Finish (or selecting "Manuel" in the "Guided Partitioning" menu) it tells me "No Root Filesystem is selected" and takes me back. Partitioning the USB Stick does not make much sense.

I found a very similar question on askubuntu: [http://askubuntu.com/questions/270505/lenovo-thinkserver-ubuntu-12-server-install-partition-issues](http://askubuntu.com/questions/270505/lenovo-thinkserver-ubuntu-12-server-install-partition-issues) But I do not understand the first answer, the poster says after confirming to use the Hardware Raid he'll partitions the disk manually but does not explain how to get there (maybe its completely different on RD330).

I know Ubuntu is not certified for this machine, but I read confirmations about people who installed Ubuntu 13.04 successfully on this model, so I think 14.04 should be possible.

I'm not very experienced in System Administration and this is my frist machine with HW RAID capabilities, so I hope someone of you is able to explain my problem and point to some solution.

Looking forward to your answers,
lg amp

---

### Post by TheFu on 2015-01-03
If you use HW-RAID, don't use mdadm (SW-RAID).

---

### Post by office.partsch on 2015-01-03
I already tried with deactivating the MDADM option. It still does not show the RAID drives.

---

### Post by TheFu on 2015-01-03
HW RAID drives don't show up inside the OS as RAID .... er ... unless you have drivers. They should show up as regular drives, I'd think.
I don't use HW RAID myself. The flexibility of SW-RAID and ability to move arrays between systems easily makes more sense for my needs. Don't need the HW-RAID performance here, but if you need it, definitely use it.

Then there is FakeRAID - lots of motherboards claim RAID support with this as their method. No reason to use FakeRAID that I know on a *clear field* install.

Can you run **bootinfo** and post the generated link? My signature has links to that script, if you need it.

---

### Post by MAFoElffen on 2015-01-03
Which Thinkserver RAID option are you using? on-board 300 -or- add-on 500, 700 or 710?

Like HP went to a few years ago, the lower end RAID options are fake-raid. It is really software RAID and you would need drivers to support it (such as with Win Server, they have a drivers disk...) 

Here is what your Lenovo Manual says about the series 300 controller:
> 
The ThinkServer RAID 300 ([COLOR=#ff0000]also known as onboard SAS software RAID[/COLOR]) is integrated in the PCH on the system board. If you connect the mini-SAS to mini-SAS signal cables from the system board to the backplane, you can configure RAID for the hard disk drives using the LSI Software RAID Configuration Utility program, independently of the operating system. The ThinkServer RAID 300 supports RAID levels 0, 1, and 10 by default. You also can activate RAID 5 by installing a ThinkServer RAID 300 Upgrade Key for Advanced RAID. See &#8220;Installing or removing the ThinkServer RAID 300 Upgrade Key for Advanced RAID&#8221; on page 125.

So since it is software RAID, that lower end controller is not recognized as an HBA (Host Bus Adapter)... so the the logical drive is not going to be seen and it is going to be seen by Linux kernel as the separate JBOD drives.

What I've recommended to HP Sys Admins who have Server Iron with that type of controller, is to either Upgrade their controllers to the next step up, which would be HBA hardware RAID... or to just config as JBOD and use mdadm. mdadm would carry you through with no additional cost. Since it is also software RAID, the same considerations.

Some vendors have rhel drivers for that type of controller, which you would load (interim) on the install to use that controller... Those drivers are very proprietary and specific in focus. I've convert some of those for some of my own iron... But keep in mind that this is a minority, because these are low-end controllers and Most vendors see that as an incentive to upgrade to their higher end controllers.

That is what I see and suspect.

---

### Post by office.partsch on 2015-01-05
Because of a deadline we had to setup Windows Server and go with virtualization. It seems to be rather complex to get the available drivers running for Ubuntu and even after accomplishing that, there are further problems with installing and running Grub...
Thanks for your support

---

### Post by TheFu on 2015-01-05
We've all been burned by Windows-only hardware support.  

Linux support for lots of hardware is better and longer, but not for all hardware.  I've been burned even by RAID HW that loudly claimed support for Linux ... support was a 2 yr old (at the time) kernel module BLOB.  If I wanted to use it, I'd have to run 2.4.x kernels. No newer support became available.  Fortunately, that card was recognized as JBOD by the kernel drivers, so all the extra ports aren't completely useless. 

Live and learn.

OTOH, printer drivers for old printers no longer supported since Vista are great under Linux.  Why should people have to buy new printers just because a 64-bit OS is released?

---

