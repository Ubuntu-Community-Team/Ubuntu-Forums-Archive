---
title: "LVM: Missing logical volume after hard drive failed"
date: 2014-11-25
forum: Server Platforms
---

### Post by Living Field on 2014-11-25
Ubuntu 14.04 Server installed on a pair of 4TB drives. One drive failed, now when the server is started, it scrolls these four lines forever:
[INDENT]incrementally starting RAID arrays...
mdadm: CREATE user root not found
mdadm: CREATE group disk not found
Incrementally started RAID arrays.[/INDENT]

It may be a while before I can replace the failed disk, so I just want to operate this server on a single drive.

The drives were identically partitioned as follows
1 - small BIOS boot partition (needed to boot a GPT disk on a BIOS computer) - 2MB
2 - mdadm RAID for /boot - 1GB
3 - LVM host for vg1 - 3.6TB (This was NOT built on top of an mdadm RAID)
4 - swap

The Volume Group vg1 contained three Logical Volumes
1 - root (RAID1 mirror -- I'm not sure if this is correct LVM terminology)
2 - home (RAID1 mirror)
3 - media (striped, no redundancy)

It appears to me that the (broken) mdadm mirror is working OK. I can get to GRUB and I can get to an initramfs prompt if I add break=premount to the grub kernel entry.

I have moved the working hard disk to my desktop computer to try to figure things out.
I can mount the "home" LV, no problem. Since the "media" LV was not redundant, it's not recoverable, but no worries there.

Here's the problem:
I can't mount the "root" LV, and I don't know why.

```
$ sudo vgchange -ay vg1 --partial
  PARTIAL MODE. Incomplete logical volumes will be processed.
  /dev/vg1/media: read failed after 0 of 4096 at 0: Input/output error
  /dev/vg1/media: read failed after 0 of 4096 at 4096: Input/output error
  Couldn't find device with uuid O91I3d-VcmK-PTDV-i4fG-h0cI-yssi-PYhkoF.
  device-mapper: reload ioctl on  failed: Input/output error
  4 logical volume(s) in volume group "vg1" now active

$ lvscan
  /dev/vg1/media: read failed after 0 of 4096 at 0: Input/output error
  /dev/vg1/media: read failed after 0 of 4096 at 4096: Input/output error
  Couldn't find device with uuid O91I3d-VcmK-PTDV-i4fG-h0cI-yssi-PYhkoF.
  ACTIVE   Original '/dev/vg1/root' [100.00 GiB] inherit
  ACTIVE            '/dev/vg1/home' [2.00 TiB] inherit
  ACTIVE            '/dev/vg1/media' [1.00 TiB] inherit
  ACTIVE   Snapshot '/dev/vg1/snap1-fresh' [10.00 GiB] inherit

$ ls /dev/vg1
home  media

$ ls /dev/mapper/
control                        vg1-root-real
vg1-home                       vg1-root_rimage_0
vg1-home_rimage_0              vg1-root_rimage_0-missing_0_0
vg1-home_rimage_0-missing_0_0  vg1-root_rimage_1
vg1-home_rimage_1              vg1-root_rmeta_0
vg1-home_rmeta_0               vg1-root_rmeta_0-missing_0_0
vg1-home_rmeta_0-missing_0_0   vg1-root_rmeta_1
vg1-home_rmeta_1               vg1-snap1--fresh-cow
vg1-media                      vg1-snap1--fresh-missing_0_0
vg1-media-missing_0_0

$ lvdisplay
  /dev/vg1/media: read failed after 0 of 4096 at 0: Input/output error
  /dev/vg1/media: read failed after 0 of 4096 at 4096: Input/output error
  Couldn't find device with uuid O91I3d-VcmK-PTDV-i4fG-h0cI-yssi-PYhkoF.
  --- Logical volume ---
  LV Path                /dev/vg1/root
  LV Name                root
  VG Name                vg1
  LV UUID                LMm8Tw-sBji-mnl0-2HoQ-pkXE-RE20-9Mox1f
  LV Write Access        read/write
  LV Creation host, time Ivy-Ubuntu, 2014-04-24 15:12:15 +0700
  LV snapshot status     source of
                         snap1-fresh [active]
  LV Status              available
  # open                 0
  LV Size                100.00 GiB
  Current LE             25600
  Mirrored volumes       2
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:7
   
  --- Logical volume ---
  LV Path                /dev/vg1/home
  LV Name                home
  VG Name                vg1
  LV UUID                JKvtFh-hi57-dBaD-mBjW-M9w6-2BTt-6SWsRF
  LV Write Access        read/write
  LV Creation host, time Ivy-Ubuntu, 2014-04-24 15:43:54 +0700
  LV Status              available
  # open                 1
  LV Size                2.00 TiB
  Current LE             524288
  Mirrored volumes       2
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:17
   
  --- Logical volume ---
  LV Path                /dev/vg1/media
  LV Name                media
  VG Name                vg1
  LV UUID                sequXg-Xm6d-ucda-PcYt-A85r-3Tdi-JIFJHh
  LV Write Access        read/write
  LV Creation host, time Ivy-Ubuntu, 2014-04-24 18:15:20 +0700
  LV Status              available
  # open                 0
  LV Size                1.00 TiB
  Current LE             262144
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     512
  Block device           252:19
   
  --- Logical volume ---
  LV Path                /dev/vg1/snap1-fresh
  LV Name                snap1-fresh
  VG Name                vg1
  LV UUID                A2J7sr-n0Ys-EKPU-QAuv-wkiv-QWjR-qAcgKW
  LV Write Access        read/write
  LV Creation host, time trusty, 2014-04-29 06:11:10 +0700
  LV snapshot status     active destination for root
  LV Status              available
  # open                 0
  LV Size                100.00 GiB
  Current LE             25600
  COW-table size         10.00 GiB
  COW-table LE           2560
  Allocated to snapshot  100.00%
  Snapshot chunk size    4.00 KiB
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:10

$ sudo vgreduce --test --removemissing vg1
  TEST MODE: Metadata will NOT be updated and volumes will not be (de)activated.
  /dev/vg1/media: read failed after 0 of 4096 at 0: Input/output error
  /dev/vg1/media: read failed after 0 of 4096 at 4096: Input/output error
  Couldn't find device with uuid O91I3d-VcmK-PTDV-i4fG-h0cI-yssi-PYhkoF.
  WARNING: Partial LV root needs to be repaired or removed. 
  WARNING: Partial LV home needs to be repaired or removed. 
  WARNING: Partial LV media needs to be repaired or removed. 
  WARNING: Partial LV snap1-fresh needs to be repaired or removed. 
  WARNING: Partial LV root_rimage_0 needs to be repaired or removed. 
  WARNING: Partial LV root_rmeta_0 needs to be repaired or removed. 
  WARNING: Partial LV home_rimage_0 needs to be repaired or removed. 
  WARNING: Partial LV home_rmeta_0 needs to be repaired or removed. 
  There are still partial LVs in VG vg1.
  To remove them unconditionally use: vgreduce --removemissing --force.
  Proceeding to remove empty missing PVs.

```

The "vgreduce --removemissing" command is pretty scarry to me. If I ran it without the --test and with the --force, would "home" and "root" be safe, or would they be deleted? Would this help me load the "root" LV?

---

### Post by oldfred on 2014-11-25
I do not know RAID nor LVM. As that is more server based.
But I thought those with LVM usually RAID that as if any drive in LVM breaks you lose the entire LVM.

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by Living Field on 2014-11-26
While I still haven't gotten the system to boot correctly, I was able to access the root LV by removing a snapshot I'd made of it. I was tipped off by an error message in the kernel log:
```
device-mapper: ioctl: error adding target to table
device-mapper: table: 252:17: snapshot: Failed to read snapshot metadata
```

I fixed this error by deleting the snapsho and then activating itt:
```
# lvremove /dev/vg1/snap1-fresh --force
  Couldn't find device with uuid O91I3d-VcmK-PTDV-i4fG-h0cI-yssi-PYhkoF.
  Logical volume "snap1-fresh" successfully removed

# lvscan
  Couldn't find device with uuid O91I3d-VcmK-PTDV-i4fG-h0cI-yssi-PYhkoF.
  inactive          '/dev/vg1/root' [100.00 GiB] inherit
  inactive          '/dev/vg1/home' [2.00 TiB] inherit
  inactive          '/dev/vg1/media' [1.00 TiB] inherit

# lvm lvchange -ay /dev/vg1/root --partial
  PARTIAL MODE. Incomplete logical volumes will be processed.
  Couldn't find device with uuid O91I3d-VcmK-PTDV-i4fG-h0cI-yssi-PYhkoF.
```

I'm still looking for how to safely delete the PV and get Ubuntu to startup.

---

### Post by Living Field on 2014-11-26
The man pages for LVM are lacking in detail, but I found a nice write-up on [LVM device fault handling]("http://mcs.une.edu.au/doc/lvm2/lvm_fault_handling.txt").
Unfortunately, it didn't help me.
Neither of these commands fixed anything:
vgreduce --removemissing --force vg1
lvconvert -mo —repair -f /vg1/root

I have figured out how to get the server running, though it's not yet automatic.

Here are the instructions I left for starting the server up while I drive 12 hours to the neighboring country to buy some new hard disks.
```
1. Press power button
2. Begin pressing ESC repeatedly. It’s OK if the computer beeps.
3. You’ll see a white-on-black “GNU GRUB” menu screen.
4. Press ‘e’ to edit the command line
5. Press DOWN 17 times to get to the line beginning with ‘linux’.
6. Press RIGHT to the space after ‘ro’
7. Insert the words ‘break=premount’ like this:
...vg1-root ro break=premount quiet spla..
8. Press ‘F10’
9. Ignore the message “diskfilter writes are not supported”
10. You’ll see an ‘(initramfs)’ prompt. Type this:
(initramfs) vgchange -a y --pa     press ENTER
(initramfs) exit                   press ENTER
11. The server will now complete starting normally
```

I think I'm going to have to give up on using mdraid or LVM. A single drive failure still takes down the system and also makes it much more complicated to get running again. I think I'll use some type of rsync script to keep a second drive as a hot spare.

---

### Post by MAFoElffen on 2014-12-04
I'm following this. Not enough to help, as I have my own challenges with this also, but learning and dabbling with it, like you.

I was hardcore hard-RAID. Hardware RAID was a no-brainer. Utitlty and capabilities were limited to what was available on BIOS. Was very spendy. That taught me about RAID itself and about strategies. Level 0 was a gamble. RAID 1 (mirrors) were safe but resource intensive. RAID 5 and 6 were nice. I used to play with purposely failing disks and rebuilding the Arrays. What it also taught me, is that RAID is not a replacement for backups.

About 3 years ago, I moved to Linux RAID. It had some challenges in the learning curve. It was definitely less expensive. I have to plan out what I wanted and learned to do it. It had less limits and more utility. 

For a while, I stayed away from LVM. It reminded me too much of RAID 0. But people raved about it and what they could do with it. It seemed to have morre fault tolerance than just RAID 0.

Last year, I forced myself to use LVM on mdadm. I figured that I needed to try it out and learn it. Now just started using LVM with redundancy (without any RAID). Maybe I just like living on the edge. I don't know.

I do snaphots... I back those snapshots over to my SANS... meaning, on to other physical disk storage. This seems to be working out for me so far. But like I said, following what you do and what happens with yours. Disk storage is cheap enough now, that I no longer back to tape. Faster and possible now, just to back to it to disk. 

Curious-- Was the snapshots you deleted on that same physical machine?

EDIT-- Another curiosity... I just got through migrating my LVM root drives to big GPT disks. Like you, I followed other people's recipe's on doing that and used vgreduce, pvmove and such... One thing not mentioned by others, was that the disks previously added by pvcreate were still in the PV and showed up in pvdisplay (as unused disks, but still being members of the pv). When I physically removed them, I would get log pv type errors, saying they were not present. I plugged those drives back in temporarily and no errors... That led me to think there was a step missing from those recipes. I used pvremove to remove those disks from the pv definitions... and have had NO errors of those type since. (Just a thought that might be related to yours.)

---

### Post by Living Field on 2014-12-07
Yes, the snapshot was on the same volume group. It was there in case I mucked up the configuration of the server.

That's interesting what you say about using pvremove. Unfortunately my drive died so I can't plug it back in. And the dead drive still holds logical volumes, so according to the man page, pvremove wouldn't work.

I bought a new drive last week while my coworker got the bad drive replaced under warranty, so I have two spares now. I'll use the holiday this week to figure out how to use clonezilla and rsync to abandon mdadm and LVM.

I don't need 24/7 reliability for this server, but I really, really need something that can be repaired easily by someone (other than me) who doesn't understand computers but can follow instructions. I think I may open a new thread for advice on this.

---

### Post by Living Field on 2014-12-07
[duplicate post deleted]

---

