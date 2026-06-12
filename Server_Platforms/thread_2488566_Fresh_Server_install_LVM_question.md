---
title: "Fresh Server install LVM question:"
date: 2023-07-09
forum: Server Platforms
---

### Post by Heeter on 2023-07-09
Hi all,

Finally did a fresh new reinstall of Ubuntu22.04LTS onto my DellR610 server. It's a 6x1.2Tera HDDs (3.2Terabytes Total) in a RAID10 config.

Only thing this server will be doing will be host the KVM vm's. I have 3 existing VM's that I am putting into the server, but it is complaining that I have run out of free space????

The VM's total is about 500gig of space required.

I believe during the install, Ubuntu LVM did not allocate the whole available space, if someone can confirm for me. (sorry I am very weak with LVM) 

```

root@serv:/media/external# fdisk -l

Disk /dev/sdc: 3.27 TiB, 3598914158592 bytes, 7029129216 sectors
Disk model: PERC H700       
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 93CAE3DE-3DED-46B7-8D32-B964D9BC495F

Device       Start        End    Sectors  Size Type
/dev/sdc1     2048       4095       2048    1M BIOS boot
/dev/sdc2     4096    4198399    4194304    2G Linux filesystem
/dev/sdc3  4198400 7029127167 7024928768  3.3T Linux filesystem

Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 100 GiB, 107374182400 bytes, 209715200 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sdd: 1.82 TiB, 2000365289472 bytes, 3906963456 sectors
Disk model: My Passport 2626
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x3802768e

Device     Boot Start        End    Sectors  Size Id Type
/dev/sdd1        2048 3906963455 3906961408  1.8T 83 Linux
root@serv:/media/external# lvdisplay
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/ubuntu-lv
  LV Name                ubuntu-lv
  VG Name                ubuntu-vg
  LV UUID                4ZnDP7-CdoK-UQan-qeR6-LEyA-KqYk-y6DoU2
  LV Write Access        read/write
  LV Creation host, time ubuntu-server, 2023-07-09 02:17:15 +0000
  LV Status              available
  # open                 1
  LV Size                100.00 GiB
  Current LE             25600
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0
   
root@serv:/media/external# lsblk
NAME                      MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
sda                         8:0    1    0B  0 disk 
sdb                         8:16   1    0B  0 disk 
sdc                         8:32   0  3.3T  0 disk 
&#9500;&#9472;sdc1                      8:33   0    1M  0 part 
&#9500;&#9472;sdc2                      8:34   0    2G  0 part /boot
&#9492;&#9472;sdc3                      8:35   0  3.3T  0 part 
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0  100G  0 lvm  /
sdd                         8:48   0  1.8T  0 disk 
&#9492;&#9472;sdd1                      8:49   0  1.8T  0 part /media/external
sr0                        11:0    1 1024M  0 rom  
sr1                        11:1    1 1024M  0 rom  
root@serv:/media/external# 


```

If I am reading this correctly, Ubuntu only used up 100Gigs?

The Second device is the usb drive that is holding the backups of the VM's

What would be my next steps? I would to have at least 1TB 

Regards

---

### Post by TheFu on 2023-07-09
Post the output from
```
sudo pvs
sudo vgs
sudo lvs
```

*display LVM commands are seldom needed.  Perhaps once a decade and only if I'm using thin provisioning. For all other LVM information, those summary commands are cleaner and easier to read in nice columns.

Also, the default options for lsblk aren't good.  Use these:
```
alias lsblkt='lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint'

```

Before you create RAID10, you need to create a partition table on all 6 disks and use a clearly, specific, size for the partition that will be used across all 6 drives. This is so when some of the drives fail, you don't have to replace them with a model HDD that isn't made anymore and can set the exact size of the partition to match what is already there.  This is a best practice.

So if a disk is 7,024,928,768b in size, I'd make the partition a little smaller, say 7020000000b, so it is clear that a specific size was chosen and used.  In 6 months or 4 yrs, when a disk fails, you'll be free to get a replacement disk that is at least that size, but can create a partition perfectly sized as the replacement.  Make sense?

BTW, 100GB is much too large for Linux OS "root" partitions.  It is fine to have a VG that size, but the "root" LV needs to be smaller. Make it tight, since adding more space to an LV is 5 seconds of time, but reducing them can require booting from alternate media.  

I assume you won't mount the RAID10 backed LVM at all and will just tell libvirt/virt-manager to use the LVM on the RAID10 as part of the KVM storage pools available.  Then you can do all sorts of great things.  While I'm not using RAID for my VM storage, I do use LVM.  Here's a layout for a VM server:
```
NAME                       TYPE FSTYPE   SIZE FSAVAIL FSUSE% LABEL    MOUNTPOINT
nvme0n1                    disk        465.8G
&#9500;&#9472;nvme0n1p1                part vfat      50M   43.2M    12% EFI      /boot/efi
&#9500;&#9472;nvme0n1p2                part ext4     600M  251.7M    49% boot     /boot
&#9492;&#9472;nvme0n1p3                part LVM2_m   465G
  &#9500;&#9472;vg00-swap              lvm  swap     4.1G                         [SWAP]
  &#9500;&#9472;vg00-root--00          lvm  ext4      35G    5.6G    79% root     /
  &#9500;&#9472;vg00-var               lvm  ext4      55G   38.6G    24% var      /var
  &#9500;&#9472;vg00-home              lvm  ext4      26G     15G    36% home     /home
  &#9500;&#9472;vg00-ubuntu2204--srv   lvm            15G
  &#9500;&#9472;vg00-ubuntu2204--srv--2lvm            15G                       
  &#9500;&#9472;vg00-Mint21.1          lvm  zfs_me    40G                rpool
  &#9500;&#9472;vg00-lxd               lvm  zfs_me    50G                lxd
  &#9500;&#9472;vg00-lv--vpn09--2004   lvm           7.5G
  &#9500;&#9472;vg00-lv--regulus       lvm            30G
  &#9500;&#9472;vg00-lv--regulus--2    lvm            10G
  &#9500;&#9472;vg00-lv--blog44        lvm          16.2G
  &#9500;&#9472;vg00-lv--xen41--1204   lvm          12.5G
  &#9492;&#9472;vg00-lv--zcs45--1604   lvm            25G
```
All those lines without any mountpoint are for use by VMs.  

You can see regulus and regulus--2?  That's an old desktop that outgrew the 30G assigned for it, so I added another 10G later.  I could have used **lvextend** to make the LV for regulus larger, but I wanted to add storage without any downtime. It was a bit of an exercise.  Interesting, but not really what I'd do again.

I wouldn't put the OS release for the initial install in the LV name either. That was a mistake that seemed like a good idea at the time. Eventually, it becomes wrong and I still have to use a script/ansible to get the actual release being run anyway.

Also, I use lxd and have a number of lxd managed lxc containers. They all share that single 50G LV.

BTW, rather than using HDDs, I'd really push for you to get an SSD. Performance will be massively better and SSDs are known for not having failures. A 1TB Samsung SSD is between $40 and $80. There have been massive price drops the last 1 months.  I paid $70 in May and the same model 1TB SSD is now $50. 
Use HDDs for backups, not the main, live, storage.

---

### Post by MAFoElffen on 2023-07-09
I saw this last night, and with a Dell MC PE, I am assuming he is using the internal PERC RAID controller card (hard RAID).  So not seeing an outside partition/container for the RAID10... The Outside container is the PERC hard-RAID logical Volume. Which he did not provide info the BIOS config from that, from iDRAC...

I started to answer this last night, with an explanation of "how LVM2 works", a further explanation of how to implement KVM storage pools on LVM2... with a recommendation to start over, aligned with your recommendation of isolating the OS on another disk..

Alas, I saw this when I got home from work at around 2am (closing shift), so thought to answer this this morning. I just woke up and made coffee.

I totally agree with TheFu...He has years of experience with LVM2 and KVM.  I have more to add, based on decades of experiences with Dell EMC Hardware, OS'es, Volume Managers, and KVM hosts. 

Like TheFu, both of us having been System Admins, we are not a fan of putting all our eggs in one basket. Doing that, you risk a single point of failure. You have a problem with your single RAID Array, then you: Destroy > Create New > Restore from your backups... I know you are not going to want to hear this, but my recommendation, along with TheFu, would be to start over from the ground up. Now, at the start is the time to do this, to make a much better system, with what you have currently.  (Maybe adding two more low-cost pieces that would transform your machine into something more modern and would enhance your performance greatly.)

The Dell PE R610 was released in 2009, where the PERC's of that time were limited to 2TB max sized HDD disks. The controller would only recognize larger disks put in it as being 2TB, so that is your hardware limit there. Also, all the drives in a logical RAID volume have to be the same size. All you can do with the hardware RAID is to create new Logical members. It had 6 2.5" hot swap drive bays, and 2 PCIe x8 gen2 slots, rated at 4000MB/s... That is your hardware limit there for internal storage... You have your drive bays fully populated with 1.2 TB drives. Dell, back then did use PCIe SSD's. You have 2 PCIe x8 slot where you add add more storage.. 

Which PERC card do you have? I'm assuming either H200, H700, or the 6/i... Right? Are your HHD's new or how old? I'm thinking when your say 1.2 T, that you are referring to 1.2 TiB / !TB, right? How much memory and of what type? (Up to 192GB (12 DIMM slots): 1GB/2GB/4GB/8GB/16GB DDR3 up to 1333MT/s)

Let me share some of my experience.

As Enterprise Architecture methodologies recommend, I separate my OS, from applications and data. (To a point) I create containers for those, where each can be easily replaced or moved, without affecting each drastically.

I used to do hardware RAID with LVM2 on top of it, over 10 years ago. That is old technology, and doesn't make sense anymore. Yes, with RAID10, you get performance enhancements of 6 times the read and 3 times the write speed, at at a cost and with some very big limitations... The storage from that is not very flexible, nor adaptable. You can create and change disks in the existing arrays... But you cannot grow, shrink nor transform RAID types.

With RAID10, after failure of 1 disk, you risk losing half your other disks on a reassemble. That is just the cold historical facts on old disks. You have whole lots less risks with other technologies.

You can some of that with software RAID (mdadm) so I migrated from using hardware RAID to mdadm, with LVM on top of that... That was old tech and methodologies, even for 12 years ago. (I have since grown up and learned to do better...)

To do that with the PERC's you might have, there is a trick you have to do. Those PERC don't support JBOD... So no OS will see a single disk, that is behind that PERC, unless it is defined in that PERC (somehow). To do JBOD with those PERC's, you define each disk as a single-disk RAID0 logical volume. PITA, but just a quark. In that manner, you make all those resources flexible and adaptable for your use. You can now change o replace a single component easily, without a single point of failure. There are now Flash images for those PERC's, where you can reflash them  to do JBOD, but no matter, you don't need to do that, just to do that...

That gives you very much more options...

Now would you like to talk further about RAID, LVM2, and KVM... And what makes more sense to come out of the dark ages with what "you have", for what you want to do?

---

### Post by Heeter on 2023-07-09
Hey Guys,

Thanks for your replies on this, Your guys recommendations at this point for my RAID config will be much appreciated. I do not require any more storage space, I would say 1.5TB will be sufficient, not including OS. Currently using approx 700GIGs, been around this level of storage for the last few years.

I am running a Dell R610 with PERC H700 Internal with 6 x 1.2 TB DELL SAS 10,000RPM in a RAID10. I don't know what year the Server is, The HDD's show a 10/2014 manufacturers date, Using 8 x 8Gigs = 96Gigs RAM, with 2 x 3.06GHz 6Core Processors. These were not the original HDDs that came with this R610, but I have them sitting in storage.

I still can change up the RAID setup right now.

I don't know how to change the partition on the disks like TheFU mentioned.

If there is any better raid array setup that I can setup with the gear I have, please let me know?

I don't mind reinstalling Ubuntu at this stage.


[img]https://i.postimg.cc/hjT62BzQ/IMG-20230709-164226.jpg[/img]

[img]https://i.postimg.cc/7ZLvwdcj/IMG-20230709-164342.jpg[/img]


Here is the output:
```

root@serv:/home/admin# pvs
  PV         VG        Fmt  Attr PSize PFree
  /dev/sda3  ubuntu-vg lvm2 a--  3.27t 3.17t
root@serv:/home/admin# vgs
  VG        #PV #LV #SN Attr   VSize VFree
  ubuntu-vg   1   1   0 wz--n- 3.27t 3.17t
root@serv:/home/admin# lvs
  LV        VG        Attr       LSize   Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  ubuntu-lv ubuntu-vg -wi-ao---- 100.00g                                                    
root@serv:/home/admin# lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
NAME                      TYPE FSTYPE       SIZE FSAVAIL FSUSE% LABEL MOUNTPOINT
sda                       disk              3.3T                      
&#9500;&#9472;sda1                    part                1M                      
&#9500;&#9472;sda2                    part ext4           2G    1.7G     7%       /boot
&#9492;&#9472;sda3                    part LVM2_member  3.3T                      
  &#9492;&#9472;ubuntu--vg-ubuntu--lv lvm  ext4         100G       0   100%       /
sdb                       disk                0B                      
sdc                       disk                0B                      
sr0                       rom              1024M                      
sr1                       rom              1024M                      
root@serv:/home/admin# 

```

---

### Post by TheFu on 2023-07-10
I know nothing about PERC or HW RAID HBAs.  Where I worked, we had SAN storage with EMC frames connected by fiber.  My Linux RAID knowledge is all SW-RAID using either mdadm or LVM.

It appears that SDB and SDC aren't really recognized. SDA is 4TB,nearly all assigned to a PV/VG with 100G for the "root" LV.  How did you fill 100GB with just an OS?  For a server, I'd be shocked if the OS would be more than 10GB total.

---

### Post by MAFoElffen on 2023-07-10
He filled it because he had te installed OS, with the KVM storage pool in the default location of /var/lib/libvirt/images, and added two VM's if about 40GB each... So with 80GB's in VM's plus about 17GB for the the OS, that probably left about 3GB's left.

He never posted any of the LVM command output to accurately display what the LVM stats and device names are yet. That commands I would have asked him besides what you posted would have been (as root)
```

pvs -v
pvscan -v
pvdisplay -v -m
vgs -v
vgscan -v
vgdisplay -v
lvs -a -o name,segtype,devices
lvscan -v
lvdisplay -v

```
Option #1 would be to leave the system as is, and to "Grow" Logical Volume ubuntu-lv to leave room for VM's to be installed in the default location. Something along the lines of
```

lvextend --resizefs -L +80%FREE /dev/mapper/ubuntu-lv  # Confirmed by the device names in the output from above

```
But there is a shortcoming of his basic design layout... Currently, he only has a single VG, with a single root LV. His swap is probably a swap file within that. His KVM VM images are limited to just image files. If he does an LVM snapshot, it's of the whole root LV...

If instead, he creates some other new LV's to split out one LV for his swap, and one for his KVM storage pool, then add those to his fstab, to mount them back into his system, then he isolated his system OS from those and his KVM storage pool can grow as needed. At the moment, he only has one logical volume, his single RAID10 array. One PV, per logical disk. Can be multiple PV's per VG, but only one VG per PV limit. Better option to do something else.... 

That is not going to leverage anything from LVM2 on using LVM itself as being able to use LV's as VM images. Nor is it going to be anything adaptable or flexible. Just one raw RAID10 storage device, with a single point of failure for all of his six 8-year-old disks... where he can only lose 1 single disk (RAID10).

My recommendation for option 2, would be to start over, at a lower level, to make things more adaptable and flexible... Using what you recommended, in adding a PCIe x M.2 NVMe adapter card to one of the two PCIe x8 lane slots, with an NVMe SSD card. He just needs to ensure he upgrades his BIOS version to r610 6.6.0 to support NVMe.

Next, define all 6 SAS drives as RAID0 single disk arrays, to pass them through the PERC card, to the system, without hard-RAID. Add GPT tables to each, with single or multiple partitions, to create LVM PV's onto.

Install his OS on partitions on the NVMe. Straight up LVM2. PV#1 > root-vg > LV's for root, and swap. PV#2 > home-vg > LV for home. Leave unneeded unallocated space for reserves. 

With the 6 PV's of the SAS drives, create a VG of LVM RAID6 with either 5 drives in the array, with 1 spare (roughly 3TB), or all 6 in the array (roughly 4TB). That would give him striping performance less than RAID10, but more than flat disks, and allow failure of 2 disks, and still be able to run degraded.

Then mount that into the system, and setup that VG as an KVM his storage pool... That would allow him to be able to create LV's as KVM Guest images, which you are a fan of.

Setting up his system that way, he can lose a disk or two, and his system is still able to come up. He can upgrade or migrate his system modularly. If he wants to later go to ZFS, he can use partitions on the NVMe for SLOG and L2ARC.

The PCIe x M.2 adapter cards are about #15 to $25. NVMe card $40 to $100. Going that way, he is also no longer limited to his current 2TB limited on those disks. And he has 2 slots he can do that on...

Doing it that way gives him much more possibilities on a mulitude of things he can do.

Then there is option #3, which is a compromise of both. Split the 6 disks on the PERC card into more than one array. oe for the OS (and other) and one for the KVM storage pool. This is going to waste a lot of space. On the PERC, it only does full disk assignments, and has RAID 0, 1, 5, 6, 10, 50, 60. With RAID 6, you need at least 4 drives (roughly 2TB). That leaves 2 to be either RAID or RAID1... Not much capacity given.

---

### Post by TheFu on 2023-07-10
Whenever I see people with old servers, I wonder why.  A $400 desktop will use 1/3rd the power and be 5x faster.  For redundancy, get 2 desktops and run them in a cluster.  Proxmox makes that relatively easy.  Throw in how ever many SSDs of the type/size needed and forgetabout old HDDs for storage.  Use them for backup needs only ... or to hold huge amounts of media.

BTW, he did post the lvs, vgs, and pvs commands+output above. Perhaps the lack of whitespace between each command hid those a bit?
I tend to have 1 PV per physical drive and 1 VG.  I don't like crossing physical storage devices with LVM, unless I'm specifically using LVM RAID.  The LVM RAID implementation creates some odd setups, so lsblk has funny output and in my testing, removing 1 of the storage devices leaves a non-booting system and it died immediately.  Hardly a good outcome for RAID protection.  OTOH, with mdadm, I've pulled disks and the system kept going, just degraded.  THAT's what I want with RAID.

Of course, no RAID replaces backups.  We always need that said in every thread. RAID solves 2 problems (or it should).  Backups solve 101-1001 problems.

---

### Post by MAFoElffen on 2023-07-10
I see that output now. LOL.

I used to be one of those using retired Server hardware. They take forever to boot up, use a lot of power and sound like an old airplane when they start (especially rack servers)!!! The novelty has worn off many years ago. I have those all in storage.

You know my new server. Form factor Mini-ATX, iCore 9, 128GB RAM, 6 SSD's. 7 NVMe's. Very small footprint. Very quite. Uses very little power.

---

### Post by Heeter on 2023-07-10
LOLOL

Hey Guys, Thanks for your inputs,

Yes, that is how I jammed up 100Gs of OS LV, not realizing that there was only 100G, and started pilling in my 300G of backed up VM's into it.

Can't put anymore cash into this server, until next summer when I will build something more modern. NVME of my dreams will have to wait, LOLOL

I think that I will just create a new 500G LV and move the VMs into there

I more quick question: on my old Ubuntu 18LTS setup on this server, i have a folder "/var/vmstorage" that held the 3 VMs (email, web, and stun/coturn servers All Ubuntu) for many years. I was told that I have to retain the same folder structure in the new Ubuntu and reinstall the backed up VM's into the same "/var/vmstorage". 

How can I create a LV named /var, when there is an existing /var in the OS LV? Will it even allow me to rename current /var to something and then move everything to the new /var when I create it?

I did back up the XML files at /etc/libvirt/qemu when I backed up the 3 VM's

I have only used 300Gigs of space since I got this server many years ago. don't need any more storage real estate 

Regards

---

### Post by TheFu on 2023-07-10
Why don't you use LVM for the storage pool of your VMs?  Don't use files.  You'll get more flexibility and a tiny bit faster performance.
On servers, I think you should have a separate /var mount using an LV just for it, but there are different opinions on that.

Here's a layout for a system I built in May.
```
NAME                              SIZE TYPE FSAVAIL FSUSE% FSTYPE      MOUNTPOINT                              
nvme0n1                         931.5G disk                            
&#9500;&#9472;nvme0n1p1                         1M part                ext2        
&#9500;&#9472;nvme0n1p2                        50M part   43.9M    12% vfat        /boot/efi
&#9500;&#9472;nvme0n1p3                       700M part  342.6M    42% ext4        /boot
&#9492;&#9472;nvme0n1p4                     930.8G part                LVM2_member 
  &#9500;&#9472;vg01-swap01                   4.1G lvm                 swap        [SWAP]
  &#9500;&#9472;vg01-root01                    35G lvm    25.9G    19% ext4        /
  &#9500;&#9472;vg01-var01                     20G lvm    16.2G    12% ext4        /var
  &#9500;&#9472;vg01-tmp01                      4G lvm     3.6G     1% ext4        /tmp
  &#9500;&#9472;vg01-home01                    10G lvm     3.9G    55% ext4        /home
  &#9500;&#9472;vg01-libvirt--01              137G lvm     2.8G    98% ext4        /var/lib/libvirt
  &#9492;&#9472;vg01-lxd--containers--01       30G lvm                             
sdb                               477G disk                                                                    
&#9492;&#9472;sdb5                          476.2G part                LVM2_member 
  &#9500;&#9472;hadar--vg-lv--vpn09--2004     7.5G lvm                             
  &#9500;&#9472;hadar--vg-lv--xen41--1204    12.5G lvm                             
  &#9500;&#9472;hadar--vg-lv--zcs45--1604      25G lvm                             
  &#9500;&#9472;hadar--vg-lxd--lv              60G lvm                 ext4        
  &#9500;&#9472;hadar--vg-lv--regulus          30G lvm                             
  &#9500;&#9472;hadar--vg-lv--regulus--2       10G lvm                             
  &#9500;&#9472;hadar--vg-lv--tp--lxd_tmeta   108M lvm                             
  &#9474; &#9492;&#9472;hadar--vg-lv--tp--lxd      32.2G lvm                             
  &#9500;&#9472;hadar--vg-lv--tp--lxd_tdata  32.2G lvm                             
  &#9474; &#9492;&#9472;hadar--vg-lv--tp--lxd      32.2G lvm                             
  &#9492;&#9472;hadar--vg-lv--blog44         16.2G lvm                             

```
Ignore sdb1 and sdb2.  See all the hadar-vg stuff?  Note that most don't have any mount point. That because the LVs are managed by libvirt for VM storage pools.  The names don't mean what they might appear to mean.  The versions are from when they were first installed, not what they are running today. Newer VMs don't get that. I've learned my lesson.

I create and mount LVs where needed.  See the  /var/lib/libvirt mount?  That's for a single Win7 VM used for financial stuff. I never bothered to switch it over to using LVM.  I like having different LVs for mounted file systems so each can have the specific mount options to improve security.  For example, /tmp/ mounts with these options:
```
$ mount |grep /tmp
/dev/mapper/vg01-tmp01 on /tmp type ext4 (rw,nosuid,nodev,noexec,relatime,stripe=32)
```
Disabling suid and exec helps security.  nodev does to, but I've never seen a kernel module/device dropped in /tmp/ before.  I have seen script kiddies create directories under /tmp/ and go wild running programs there, if it is allowed. That noexec mount option stops them immediately.

All this is running on a $120 hexacore Ryzen that NEVER breaks a sweat, even when busy.  There are also 5+ LXC containers running. I have another nearly identical system with the same Ryzen and RAM that can be used to run everything on both systems concurrently.

---

### Post by Heeter on 2023-07-10
Thanks theFU I appreciate all your help

I will do that instead, Regards

---

### Post by MAFoElffen on 2023-07-11
Please do like theFu recommended. You will be very happy with that...

Which means, if you resized your existing partitions to created some more PV's, VG's and LV's to reorg similar to his...

Warining on Folder "/tmp". In Linux, that folder is for temporary files (big period)... and that folder gets flushed / deleted during boot-up. It is not for persistent files. As a DEV, I use that folder for things I don't care about and expect them to be gone. Like to create a variable that is easy to read and manipulate, that will stay around for one life cycle...

For KVM, there are 2 important folders to remember:
```

/var/lib/livirt/images   # This is the default for the VM's Image files... their virtual hard disks.
/etc/libvirt/qemu        # This is the default folder where all the VM's XML config definitions are kept for each machine.

```
If you create an LV for the XML folder to store your Domain XML files, and remount it to /etc/libvirt/qemu... then check it like this
```

mafoelffen@Mikes-B460M:~$ ls /etc/libvirt/qemu
console01.xml                    prt-003-02-1604.xml
fedora37.xml                     prt-003-02.xml
fedora38.xml                     risc64-01.xml
freebsd13.1.xml                  rollingrino22.04-1.xml
iso-tester-01.xml                solaris11.xml
kaisenrollingrino22.04-1.xml     tiny11-01.xml
kaisenrollingrino-23.04-03.xml   ubuntu14.04-2.xml
linux2020-2.xml                  ubuntu14.04-3.xml
lunar23.04-2.xml                 ubuntu14.04.xml
lunar23.04-3.xml                 ubuntu16.04.xml
lunar-efi-01.xml                 ubuntu18.04.xml
lunar-lander-00.xml              ubuntu20.04-s390x-2.xml
lunar-lander-01-01.xml           ubuntu20.04.xml
lunar-lander-01.xml              ubuntu22.04-10.xml
lunar-lander-04.xml              ubuntu22.04-11.xml
lunar-lander-05.xml              ubuntu22.04-12.xml
lunar-lander-07-01.xml           ubuntu22.04-13.xml
lunar-lander-07.xml              ubuntu22.04-14.xml
lunar-lander-08.xml              ubuntu22.04-2.xml
lunar-lander-10.xml              ubuntu22.04.2-xrdp-test.xml
lunar-lander-zfs.xml             ubuntu22.04-3.xml
lunar-server-01.xml              ubuntu22.04-4.xml
lunar-server-03.xml              ubuntu22.04-5.xml
lunar-server-04.xml              ubuntu22.04-6.xml
lunar-server-06.xml              ubuntu22.04-7.xml
lunar-server-22.04-zfs.xml       ubuntu22.04-8.xml
lunar-server-cloudimg-amd64.xml  ubuntu22.04-9.xml
lunar-server-lightvnc.xml        ubuntu22.04.xml
lunar-server-template.xml        ubuntu23.04-4-zfs-luks2.xml
lunar-server-zfs-23.04.xml       ubuntu2-lvm2-luks-00.xml
lvm-tes-22.04-svr1.xml           ubuntu-core22-20221218.xml
networks                         ubuntu-guest.xml
penryn-01.xml                    ubuntu-server-22.04.2.xml
proxmox-7.3-1.xml                win11-RMS.xml
prt_001.xml                      win2k22.xml
prt_002.xml                      xubuntu20.04-2.xml
prt-003-01-1604.xml              xubuntu22.04-01.xml

mafoelffen@Mikes-B460M:~$ ls /etc/libvirt/qemu/networks
autostart    host-bridge.xml.original  Isolated-196-168-1-0.xml
default.xml  Isolated-172-16-10-0.xml

mafoelffen@Mikes-ThinkPad-T520:~$ ls /etc/libvirt/qemu
android-x86-9.0.xml              ubuntu20.04-minx-02.xml
debian11.xml                     ubuntu20.04.xml
fedora.xml                       ubuntu20.04-ZFS-02.xml
lunar-lander-testbed.xml         ubuntu20.04-ZFS-tester.xml
macOS-Simple-KVM.xml             ubuntu20.04-ZFS.xml
networks                         ubuntu22.04-2-R5.xml
solaris11.xml                    ubuntu22.04-2.xml
ubuntu18.04-aarch64.xml          ubuntu22.04.xml
ubuntu20.04-10.xml               ubuntu-aarch64-template.xml
ubuntu20.04-11.xml               win11.xml
ubuntu20.04-2.xml                windows10.xml
ubuntu-2004-aarch64-Desktop.xml  windows11-Unsupported.xml
ubuntu-2004-aarch64.xml

mafoelffen@Mikes-ThinkPad-T520:~$ ls /etc/libvirt/qemu/networks
autostart    Isolated_Net_192.xml  Routed_Net_172.xml
default.xml  NAT_Network_172.xml

```
See, there are all the Guest's Domain Configuration files, and all the virtual network configuration files... This location is hard coded for KVM to look into that path/folder to find those... But if you either mount an LV or partition to that folder, or symlink it from there, then that works and makes that portable.

Then create a VG attach to a partition, just for /var/lib/libvirt/images... You just add the Storage Pool to KVM and point it to that location... Or anywhere else in the system tree. KVM Storage pools do not have to be in that folder, They can be changed and reconfigured.

Then both those are then "portable"... meaning that if your OS goes south, and you have to reinstall your system, or if your upgrade your system, those pieces are still there unchanged. You can move them around to your new.

With LVM, you can then take LVM snapshots of your Guest configs, and their virtual disks. One other Storage pool that I create, make portable, point to in my config's is a folder I call "ISO". That is my ISO, clean images, cloud images, BIOS Images, UART binaries folder that I use to do installs. Also in there, I keep ISO's of utilities like GParted Live & boot-repair, etc. KVM doesn't want to let you take VM snapshots of machines with UEFI BIOS (I don't understand completely the why of that), but doing things like this, you can then use the Volume Manager (itself) to make your snapshots instead.

You can see that after a few decades of doing that, making a plan to keep things organized and portable, makes thing much simpler in the long run. Organizing things a but will save you lots of work, and save your behind if there is a problem down the road. This also makes it easier to move to another machine (in the future).

In the past, I have done the same things as TheFu does with LVM2 with KVM, but now I do them with ZFS. (Another Volume Manager.)

Wherever these are "point to", these are the locations that I tell people to backup for KVM. With that, you can restore all your hard work. Or move that to another machine. There is one more location, but tha only affect if you are using VM pre-, during, and post- scripts for your VM's. Like for doing pass-throughs.

---

### Post by MAFoElffen on 2023-07-11
Or pass-through the disks through the PERC HBA... That would open up a lot of possibilities in what you can do with your storage, than just using it in full disk segments. Partitions are just storage containers. Which you can further nest with other files storage containers, to be creative with your storage needs. 

Yes. Lot's of choices and options.

To give you ideas, think in "abstract". Linux treats most 'everything' as a file system... Because of that, you can get very creative in how you make it look like a single system. Tomorrow I'm reinstalling and upgrading this 1TB drive to 2TB...
```

mafoelffen@Mikes-ThinkPad-T520:~$ lsblk -e 7 -o name,label,size,mountpoint,model
NAME   LABEL       SIZE MOUNTPOINT             MODEL
sda                1.8T                        Samsung SSD 870 QVO 2TB
&#9500;&#9472;sda1 {SYSTEM}    550M /boot/efi              
&#9500;&#9472;sda2             128M                        
&#9500;&#9472;sda3 {Windows}   900G                        
&#9500;&#9472;sda4             983M                        
&#9500;&#9472;sda5              30G                        
&#9492;&#9472;sda6           931.4G /                      
sdb                1.8T                        Samsung SSD 870 QVO 2TB
&#9500;&#9472;sdb1           931.5G                        
&#9492;&#9472;sdb2           931.5G /home/mafoelffen/Disk2 
[COLOR=#ff0000]sdc              931.5G                        Dogfish SSD 1TB
&#9492;&#9472;sdc1 mSATA1    931.5G /home/mafoelffen/mSATA [/COLOR]

```
So a Thinkpad laptop with 6TB internal storage... Possible later, with $, replacing the 2 x QVO 2TB's with QVO 8TB drives, up to 20TB internal storage on a laptop...

With that reinstall, I'm reinstalling onto a volume manager, while reorganizing my storage locations. Set things up, then install and restore back onto it.

---

### Post by Heeter on 2023-07-11
WOW, Thank you for the great info and ideas, I am just starting over right now, and using yours and ThFUs recommendations.

There is going to give me a lot of flexibility,.

Thank you so much MAFoElffen

Regards

---

### Post by TheFu on 2023-07-11
> **Heeter said:**
> Thanks theFU I appreciate all your help

I will do that instead, Regards

Your needs are probably a little different, but I've found going with smaller LVs initially to be the best choice.  Did you notice how little of the 1TB NVMe storage I'm actually using?  

BTW, I saw the same type of NVMe storage today for $45 - same brand, actually a little better model than I paid $70 for in may.  2TB is $100. These are Samsung 980 PRO SSDs - not some odd brand.  I will admit to looking at some WD-Black SSDs from the BLACK line, not to be confused with all the WD "black" colored storage they have been deceptively advertising for lesser quality storage. Beware. Those seems to have lots of performance.  I'm not looking too closely at gen3 vs gen4 NVMe stuff. It doesn't matter to me. Perhaps the cheap gen3 is all being discounted to clear stock?  Win for us!

Just remember that VG names have to be unique inside any system. So if you ever need to move a disk with LVM on it to another system, you cannot have VG names that already exist.  Part of this is why I use vg01 on 1 system and vg00 on another.  In 4 yrs, if I need to replace the storage, I may not choose to use pvmove (though pvmove is AWESOME!), and may instead migrate data using a USB enclosure for the SSD.  Just never know.

---

### Post by MAFoElffen on 2023-07-12
Other ideas, once you get those passed through... This was an LVM test machine I built for my test suite, to test my scripts and contributions.
```

root@lvm-raid-test-01:/home/mafoelffen# lvs -o name,devices,seg_type
  LV      Devices                                                                                             Type  
  lv-home lv-home_rimage_0(0),lv-home_rimage_1(0),lv-home_rimage_2(0),lv-home_rimage_3(0),lv-home_rimage_4(0) raid6 
  lv-root lv-root_rimage_0(0),lv-root_rimage_1(0)                                                             raid1 
  lv-swap /dev/sda3(0)                                                                                        linear

root@lvm-raid-test-01:/home/mafoelffen# lsblk -e 7 -o name,label,size,fstype,mountpoint
NAME                           LABEL                           SIZE FSTYPE      MOUNTPOINT
sda                                                             10G             
&#9500;&#9472;sda1                         EFI                           749.6M vfat        /boot/efi
&#9500;&#9472;sda2                                                           2G ext4        /boot
&#9492;&#9472;sda3                                                         7.3G LVM2_member 
  &#9492;&#9472;vg--swap-lv--swap                                            4G swap        [SWAP]
sdb                                                             20G             
&#9492;&#9472;sdb1                                                          20G LVM2_member 
  &#9500;&#9472;vg--root-lv--root_rmeta_0                                    4M             
  &#9474; &#9492;&#9472;vg--root-lv--root                                         18G ext4        /
  &#9492;&#9472;vg--root-lv--root_rimage_0                                  18G             
    &#9492;&#9472;vg--root-lv--root                                         18G ext4        /
sdc                                                             20G             
&#9492;&#9472;sdc1                                                          20G LVM2_member 
  &#9500;&#9472;vg--root-lv--root_rmeta_1                                    4M             
  &#9474; &#9492;&#9472;vg--root-lv--root                                         18G ext4        /
  &#9492;&#9472;vg--root-lv--root_rimage_1                                  18G             
    &#9492;&#9472;vg--root-lv--root                                         18G ext4        /
sdd                                                             10G             
&#9492;&#9472;sdd1                                                          10G LVM2_member 
  &#9500;&#9472;vg--home-lv--home_rmeta_0                                    4M             
  &#9474; &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
  &#9492;&#9472;vg--home-lv--home_rimage_0                                 6.7G             
    &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
sde                                                             10G             
&#9492;&#9472;sde1                                                          10G LVM2_member 
  &#9500;&#9472;vg--home-lv--home_rmeta_1                                    4M             
  &#9474; &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
  &#9492;&#9472;vg--home-lv--home_rimage_1                                 6.7G             
    &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
sdf                                                             10G             
&#9492;&#9472;sdf1                                                          10G LVM2_member 
  &#9500;&#9472;vg--home-lv--home_rmeta_2                                    4M             
  &#9474; &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
  &#9492;&#9472;vg--home-lv--home_rimage_2                                 6.7G             
    &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
sdg                                                             10G             
&#9492;&#9472;sdg1                                                          10G LVM2_member 
  &#9500;&#9472;vg--home-lv--home_rmeta_3                                    4M             
  &#9474; &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
  &#9492;&#9472;vg--home-lv--home_rimage_3                                 6.7G             
    &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
sdh                                                             10G             
&#9492;&#9472;sdh1                                                          10G LVM2_member 
  &#9500;&#9472;vg--home-lv--home_rmeta_4                                    4M             
  &#9474; &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
  &#9492;&#9472;vg--home-lv--home_rimage_4                                 6.7G             
    &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
sdi                                                             10G             
&#9492;&#9472;sdi1                                                          10G LVM2_member 
sdj                                                             10G             
&#9492;&#9472;sdj1                                                          10G LVM2_member 

```

---

### Post by Heeter on 2023-07-12
> **MAFoElffen said:**
> Other ideas, once you get those passed through... This was an LVM test machine I built for my test suite, to test my scripts and contributions.
```

root@lvm-raid-test-01:/home/mafoelffen# lvs -o name,devices,seg_type
  LV      Devices                                                                                             Type  
  lv-home lv-home_rimage_0(0),lv-home_rimage_1(0),lv-home_rimage_2(0),lv-home_rimage_3(0),lv-home_rimage_4(0) raid6 
  lv-root lv-root_rimage_0(0),lv-root_rimage_1(0)                                                             raid1 
  lv-swap /dev/sda3(0)                                                                                        linear

root@lvm-raid-test-01:/home/mafoelffen# lsblk -e 7 -o name,label,size,fstype,mountpoint
NAME                           LABEL                           SIZE FSTYPE      MOUNTPOINT
sda                                                             10G             
&#9500;&#9472;sda1                         EFI                           749.6M vfat        /boot/efi
&#9500;&#9472;sda2                                                           2G ext4        /boot
&#9492;&#9472;sda3                                                         7.3G LVM2_member 
  &#9492;&#9472;vg--swap-lv--swap                                            4G swap        [SWAP]
sdb                                                             20G             
&#9492;&#9472;sdb1                                                          20G LVM2_member 
  &#9500;&#9472;vg--root-lv--root_rmeta_0                                    4M             
  &#9474; &#9492;&#9472;vg--root-lv--root                                         18G ext4        /
  &#9492;&#9472;vg--root-lv--root_rimage_0                                  18G             
    &#9492;&#9472;vg--root-lv--root                                         18G ext4        /
sdc                                                             20G             
&#9492;&#9472;sdc1                                                          20G LVM2_member 
  &#9500;&#9472;vg--root-lv--root_rmeta_1                                    4M             
  &#9474; &#9492;&#9472;vg--root-lv--root                                         18G ext4        /
  &#9492;&#9472;vg--root-lv--root_rimage_1                                  18G             
    &#9492;&#9472;vg--root-lv--root                                         18G ext4        /
sdd                                                             10G             
&#9492;&#9472;sdd1                                                          10G LVM2_member 
  &#9500;&#9472;vg--home-lv--home_rmeta_0                                    4M             
  &#9474; &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
  &#9492;&#9472;vg--home-lv--home_rimage_0                                 6.7G             
    &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
sde                                                             10G             
&#9492;&#9472;sde1                                                          10G LVM2_member 
  &#9500;&#9472;vg--home-lv--home_rmeta_1                                    4M             
  &#9474; &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
  &#9492;&#9472;vg--home-lv--home_rimage_1                                 6.7G             
    &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
sdf                                                             10G             
&#9492;&#9472;sdf1                                                          10G LVM2_member 
  &#9500;&#9472;vg--home-lv--home_rmeta_2                                    4M             
  &#9474; &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
  &#9492;&#9472;vg--home-lv--home_rimage_2                                 6.7G             
    &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
sdg                                                             10G             
&#9492;&#9472;sdg1                                                          10G LVM2_member 
  &#9500;&#9472;vg--home-lv--home_rmeta_3                                    4M             
  &#9474; &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
  &#9492;&#9472;vg--home-lv--home_rimage_3                                 6.7G             
    &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
sdh                                                             10G             
&#9492;&#9472;sdh1                                                          10G LVM2_member 
  &#9500;&#9472;vg--home-lv--home_rmeta_4                                    4M             
  &#9474; &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
  &#9492;&#9472;vg--home-lv--home_rimage_4                                 6.7G             
    &#9492;&#9472;vg--home-lv--home                                         20G ext4        /home
sdi                                                             10G             
&#9492;&#9472;sdi1                                                          10G LVM2_member 
sdj                                                             10G             
&#9492;&#9472;sdj1                                                          10G LVM2_member 

```



LOLOL, Stop making LVM look so easy, MAFoElffen

Now your are just showing off, HAHAHA

Just Kidding, Thank you for all your assistance, MAFoElffen

Regards

---

### Post by TheFu on 2023-07-13
> **Heeter said:**
> LOLOL, Stop making LVM look so easy, MAFoElffen

Now your are just showing off, HAHAHA

Just Kidding, Thank you for all your assistance, MAFoElffen

Regards

The sdb and sdc stuff is what happens when you use LVM-RAID1.  That is the "ugly" view that I've been mentioning. LVM-RAID is a bit of a hack, IMHO.  Perhaps lsblk could display the output cleaner?  IDK.

The /home LVM stuff is probably RAID5/6-LVM?  I didn't count nor look at the lsv summary.

Ugly.

---

### Post by MAFoElffen on 2023-07-13
Yes, RAID6... LVM RAID also lets you set "RAID policies". Where, as you said you liked, you can pull two drives, and it continues to function as degraded.

LVM RAID uses MDRAID from the kernel. So when I explain the Russian Nested Dolls model, it just puts it inside of the LVM storage containers. It really extends mdadm in good LVM kinds of ways. It's like using mdadm, but with LVM commands.

With LVM2 RAID you can grow and shrink arrays on the fly. You can also transform array types. That's some 'things' you cannot do with hard raid, and some you can do with mdadm, but not as easily.

He (currently) has 6 very fast, very big, SAS drives. The expected lifespan on them is silly. You and I would not span them in a linear fashion (RAID0 or Multiple PV's to one VG). That is just not smart. To do that safely, why not do a RAID 6 storage pool, right? Or for me in ZFS, RAID-Z2 or RAID-Z3 which can do 2-3 disk failures and is self-healing...

It's a balance in reliability, performance, and capacity. I am not a fan of RAID for an OS system drive. You can get up quicker just thinking of that drive as disposable, and replaceable to get back up quicker. The others outside that can be managed as a storage pool safely. I just spun up that example, to show what can be done safely with 6 drives.

EDIT: I reread this and had more to expand on treating the OS drive as disposable. In my last admin role, for the main server that held all the other pieces together, I had another system drive setup, that could be swapped in to bounce the server and bring everything back up again. That company couldn't afford a fail-over cluster, but they could afford a spare drive. That was my answer to that. Less than 2 minutes downtime. You can do that if you separate the pieces out, that is still designed to work together.

---

### Post by TheFu on 2023-07-13
I tested my RAID1-LVM setup with a virtual machine by disconnecting the 2nd drive.  I expected it would keep running and that boot would work.

Just did this again, removed vdb completely from the system, and booted. It worked as expected. No complaints.  I do recall that it failed last test. Perhaps I was hallucinating? 

Then after adding the drive back and rebooting again ...

```
$ sudo lvs
  LV      VG    Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  lv-0    vg-00 rwi-ao**r**--- 10.00g                                    **100.00**          
  lv-swap vg-00 -wi-ao----  1.00g                                                    

$ lsblkt
NAME                       SIZE TYPE FSTYPE      LABEL MOUNTPOINT
vda                         15G disk                   
&#9500;&#9472;vda1                       1M part                   
&#9500;&#9472;vda2                     768M part ext4              /boot
&#9492;&#9472;vda3                    13.2G part LVM2_member       
  &#9500;&#9472;vg--00-lv--0_rmeta_0     4M lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9500;&#9472;vg--00-lv--0_rimage_0   10G lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9492;&#9472;vg--00-lv--swap          1G lvm  swap              [SWAP]
vdb                         15G disk                   
&#9500;&#9472;vdb1                       1M part                   
&#9500;&#9472;vdb2                     768M part                   
&#9492;&#9472;vdb3                    13.2G part LVM2_member       
  &#9500;&#9472;vg--00-lv--0_rmeta_1     4M lvm                    
  &#9474; &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /
  &#9492;&#9472;vg--00-lv--0_rimage_1   10G lvm                    
    &#9492;&#9472;vg--00-lv--0          10G lvm  ext4              /

$ dft
Filesystem               Type  Size  Used Avail Use% Mounted on
/dev/mapper/vg--00-lv--0 ext4  9.8G  4.5G  4.8G  49% /
/dev/vda2                ext4  739M  398M  288M  59% /boot


```

This is just a little play 22.04 server for just this sort of test, so no fancy production-like LVs.  Actually, the 2 storage devices are from the exact same SSD, so it isn't really redundant at all, but the VM doesn't know that. Sorry.

---

### Post by MAFoElffen on 2023-07-14
LMAO!!!! I loved that! Thank you. I really needed that right now!

---

### Post by TheFu on 2023-07-14
Heeter?  You still here?  
MAFoElffen and I get off topic pretty fast sometimes. ;)

---

