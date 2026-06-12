---
title: "Slow LVM2 lv-to-lv copy"
date: 2011-07-16
forum: Server Platforms
---

### Post by HuckBerry on 2011-07-16
I've got three disks together on a *home* server that constitute four LVs.

The two are the root and swap LVs installed by the Ubuntu 10.04.2 LTS installer on the OS drive (250 GB VG: Beta). The third & fourth LVs I made of two physical volumes (640 GB and 200 GB VG: Data) and mounted each inside /torrent. All are ext4.

I'm migrating lots of large files from /home to inside of /torrent, but I'm seeing EXTREMELY slow speeds (700KB/s).

I'll admit this is my first time using LVM, and I tried it only because of the numerous smaller drives I have sitting around that weren't getting used. I didn't expect such a large drop in speed.

Here's a more technical review of the setup:
```

me@Beta:~$ sudo pvdisplay
[sudo] password for me: 
  --- Physical volume ---
  PV Name               /dev/sdb
  VG Name               Data
  PV Size               596.17 GiB / not usable 344.00 KiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              152620
  Free PE               0
  Allocated PE          152620
  PV UUID               tjK28P-3hkT-Wyc7-V8U2-T7Fk-Fy0u-KARBKf
   
  --- Physical volume ---
  PV Name               /dev/sdc
  VG Name               Data
  PV Size               186.31 GiB / not usable 2.21 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              47695
  Free PE               21115
  Allocated PE          26580
  PV UUID               Jgdv3x-ksya-SJK4-vdMd-Uu5t-BMK7-Cu1Hmy
   
  --- Physical volume ---
  PV Name               /dev/sda5
  VG Name               Beta
  PV Size               232.65 GiB / not usable 2.00 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              59557
  Free PE               1
  Allocated PE          59556
  PV UUID               LxJGmB-1OAt-0mmr-Ma3F-hzmL-u8w7-wGOKnY
me@Beta:~$ sudo lvdisplay
  --- Logical volume ---
  LV Name                /dev/Data/BTN
  VG Name                Data
  LV UUID                duSvjb-VT01-1y05-RzMr-Zyf9-Kfsj-3T5qJd
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                350.00 GiB
  Current LE             89600
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:0
   
  --- Logical volume ---
  LV Name                /dev/Data/PTP
  VG Name                Data
  LV UUID                0U3UwG-Tv3q-n6ZS-fdej-2O10-py2n-GATPME
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                350.00 GiB
  Current LE             89600
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:1
   
  --- Logical volume ---
  LV Name                /dev/Beta/root
  VG Name                Beta
  LV UUID                6yYXDu-8f3O-GR3T-EtLN-vUA3-4OTn-442nD0
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                229.79 GiB
  Current LE             58825
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:2
   
  --- Logical volume ---
  LV Name                /dev/Beta/swap_1
  VG Name                Beta
  LV UUID                kyLMq2-jspv-iFTA-3pHO-OJWl-mUrM-hVRZMS
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                2.86 GiB
  Current LE             731
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           251:3

```

---

### Post by psusi on 2011-07-16
How are you moving the files?

---

### Post by HuckBerry on 2011-07-17
I added the root filesystem as an ssh share (sftp is the protocol I think) and then dragged an dropped. The 700 MB/s reading is from Ubuntu's file operation dialog. I'm not sure if this would implement a disk-to-disk transfer (as I hoped) or if this now made it an over-the-loopback-interface style transfer.

Further on this point, I'm 24 hours into the copy and only 33% done, is there any way for me to shut down this machine (which has nothing to do with the transfer other than issuing the sftp command) which wont kill the transfer in progress?

---

### Post by psusi on 2011-07-17
Wait, when did a network come into this picture?  I thought this was local disk to local disk?

---

### Post by HuckBerry on 2011-07-18
might have slipped my mind in the first post. The LVM is on Beta which is my secondary server. I'm on my desktop and I attached the root of Beta's filesystem as an sftp share on my desktop so I could graphically drag-and-drop the folders instead of having to command-line-fu it all over. Both disks are on Beta so the transfer is disk-to-disk. I didn't think much of the sftp because I figured I'd go to bed and it'd be done in the morning. I was very wrong.

I've left my desktop on because I believe shutting down would stop the transfer, but the desktop itself isn't really contributing to the copy at all so it'd be nice to "detach" from the transfer and let it do it's stuff while I shut the desktop down.

EDIT://

Just took a peak at iftop because I had a sneaking suspicion at what was going on. I hate being right. I've got 6 Mbps coming in and out of my wireless interface, so the sftp is actually copying from Beta to my desktop and then back again. Whoever coded that was an idiot. There should be a test for disk-to-disk and then it should be implement with something other than ftp.

Unrelated note: 6 mbps? wtf. N wireless card + N router = > 6mbps.... The network is empty other than these devices. Even if you count both directions (6 in + 6 out = 12 total) that's still pretty lame.

---

### Post by psusi on 2011-07-18
Yes, if you want to copy it on the server, then you need to ssh to the server and copy it there.

---

