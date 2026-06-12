---
title: "Ubuntu Server Partitioning"
date: 2022-02-17
forum: Server Platforms
---

### Post by Matthew_Wells on 2022-02-17
So I am very new to all of this. I recently installed Ubuntu Server on an old PC and let it do the automatic partitioning during setup and it only partitioned in 200GB out of the 1TB on the NVME. Is there a reason for this and how can I go about reclaiming that lost space without messing anything up?

> lsblk
NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop0                       7:0    0  43.1M  1 loop /snap/certbot/1788
loop1                       7:1    0 110.8M  1 loop /snap/core/12725
loop2                       7:2    0  61.9M  1 loop /snap/core20/1328
loop3                       7:3    0  55.5M  1 loop /snap/core18/2284
loop4                       7:4    0  67.2M  1 loop /snap/lxd/21835
loop5                       7:5    0  43.6M  1 loop /snap/snapd/14978
loop6                       7:6    0   228M  1 loop /snap/rocketchat-server/1511
loop7                       7:7    0  55.4M  1 loop /snap/core18/2128
loop8                       7:8    0  70.3M  1 loop /snap/lxd/21029
loop9                       7:9    0 227.9M  1 loop /snap/rocketchat-server/1510
sda                         8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1                      8:1    0     1G  0 part 
&#9492;&#9472;sda2                      8:2    0 464.8G  0 part 
  &#9500;&#9472;rl-swap               253:1    0   7.9G  0 lvm  
  &#9500;&#9472;rl-home               253:2    0 386.9G  0 lvm  
  &#9492;&#9472;rl-root               253:3    0    70G  0 lvm  
sr0                        11:0    1  1024M  0 rom  
nvme0n1                   259:0    0 931.5G  0 disk 
&#9500;&#9472;nvme0n1p1               259:1    0     1M  0 part 
&#9500;&#9472;nvme0n1p2               259:2    0     1G  0 part /boot
&#9492;&#9472;nvme0n1p3               259:3    0 930.5G  0 part 
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0   200G  0 lvm  /

---

### Post by MAFoElffen on 2022-02-18
> **Matthew_Wells said:**
> <<<Quote from you editted>>>

...it only partitioned in 200GB out of the 1TB on the NVME. Is there a reason for this and how can I go about reclaiming that lost space without messing anything up?

> lsblk | grep -v 'loop'
NAME                      MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                         8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1                      8:1    0     1G  0 part 
&#9492;&#9472;sda2                      8:2    0 464.8G  0 part 
  &#9500;&#9472;rl-swap               253:1    0   7.9G  0 lvm  
  &#9500;&#9472;rl-home               253:2    0 386.9G  0 lvm  
  &#9492;&#9472;rl-root               253:3    0    70G  0 lvm  
sr0                        11:0    1  1024M  0 rom  

nvme0n1                   259:0    0 931.5G  0 disk      # NVMe, 931G Total 
&#9500;&#9472;nvme0n1p1               259:1    0     1M  0 part 
&#9500;&#9472;nvme0n1p2               259:2    0     1G  0 part /boot
&#9492;&#9472;nvme0n1p3               259:3    0 930.5G  0 part    # Partition 3. 930.5G
  &#9492;&#9472;ubuntu--vg-ubuntu--lv 253:0    0   200G  0 lvm  / # LV is 200G, unused is 730.5G.

So I don't know exactly why it only made an LV of less than 30% in that partition, but you "could" grow the LV, then the filesystem within it...

---

### Post by Matthew_Wells on 2022-02-18
Any advice on course of action for doing such? I've only messed with partitions and such and don't know much about LVs?

---

### Post by LHammonds on 2022-02-18
This is the high-level summary of what you do:

1. BACKUP YOUR DATA
2. BACKUP YOUR DATA
3. BACKUP YOUR DATA
4. Use vgdisplay to check and see how much free space you have available but unallocated.
5. If your space is in the Logical Volume (LV) but unused (free) then you just need to add it to the LV you want.  Use lvscan to see what LVs you have and how much space is already allocated.
6. Next, you run an lvextend command to allocate a specific amount that is free (as noted in the vgdisplay command)
7. Once you have expanded your LV, you then expand your File Space (FS) in the LV using resize2fs

You selected what is referred to as the "atomic partition" which means a single LV where everything shares the same space.  I guess that is OK for a single user of a desktop but I would never use that scenario on a server.  I like to isolate growth areas onto their own partitions so if they grow unexpectedly and fill up, they do not fill up the root drive which would cause OS instability.  I am certainly not saying you need to re-do anything but I will link you to my server setup article that covers the commands I've used to expand storage (vgdisplay, lvscan, lvextend, resize2fs).

Here is the [Volume / Disk Management]("https://hammondslegacy.com/forum/viewtopic.php?p=814#p814") section of my tutorial.   Also keep in mind that how I add drives into the same LV is NOT best practice for most scenarios since a disk failure can cause loss of data for the LV which have other drives in it....but in my scenario, I have a NAS and the disks are all virtual so there is almost no risk to a "drive" failing at the virtual machine level.

In your scenario, you are not trying to add more drives, you are just trying to make use of the space for the existing drive.

LHammonds

---

### Post by MAFoElffen on 2022-02-19
He is talking about a shiny brand new fresh installation of this sever... Where he can just reinstall or fix what is there.. Sounded like he just got through with the install, right? 

Yes, there are only 5 commands to know to change the size of LVM.

---

### Post by TheFu on 2022-02-22
Storage setup is a very personal thing.  Putting all of it into a single file system goes against all the "best practice" document I've ever seen.  

200G for / is just crazy, IMHO.

With LVM, the main rule is to only allocate what you need, where you need it, when you need it.  Going larger is trivial - 5 seconds, 1 command. Going smaller is a hassle and can require booting from alternate media. Downtime should be avoided and LVM is a key part of that capability, but only if allocated in a smart way.

If I'm doing a fresh install, I want the OS separate from user data and separate from logs and separate from commercial program file systems.  Each of those should be a separate file system, IMHO.  This will aid backups.

root-lv 35G, not larger.  Especially on a server, it is likely that only 2-10G will be needed for programs.  If you need more later, you can increase the root-lv easily. Even on a bloated Ubuntu/Gnome3 desktop, 35G is huge.

var-lv is where logs go.  Logs can run-away and if logs are in the same LV as root-lv, then the system can crash. Start with 4G.
home-lv is where some judgement comes in. Think starting with 50G is fine. 
swap-lv is dependent on the workload and how tight RAM is.  For a server, we want to minimize the use of swap, but due to some kernel optimizations, some swap is best, perhaps 500MB to 1000MB.  For a desktop, there's only 1 answer for swap - 4GB. The point of swap is to let users "feel" the system getting slower, so they can close programs. Swap doesn't replace RAM, even NVMe is still 10000x slower than RAM. Too much swap is just as bad as too little.

Some of the SSD will be necessary for snapshots. This is how people using LVM make backups.  Chances are that the term "snapshots" you are used to hearing is not the same.  In advanced volume management, a snapshot is a frozen block of storage that cannot be modified.  BTRFS, LVM and ZFS all provide snapshots.  Backup tools may claim to "take snapshots", but this is completely different.  With LVM, we create a snapshot at the LV level, then mount that snapshot (frozen blocks) and have a backup took backup the snapshot to different storage or over the network. We can retain the snapshot or delete it. I've seen where people keep snapshots for a week, since they can be used to rollback to that point in time almost instantly.  Creating a snapshot just prior to performing a huge system patch can make rolling back very easy. You'll want to read up on snapshots, since I've simplified the explanation above to be easier to understand, not completely technically correct.  

If you have storage that multiple users need to share, say for a project team working together, you'll want to keep that outside their HOME, but in a place they all have write access.  I've been using /d/D1 - /d/D9 for different project teams.  Normally, this extra storage holds huge data or media files, so I'd never place that on NVMe or even SATA-SSD storage. Most clients get an NFS mount to a storage server.

I've posted disk layouts here many times including LVM, so please search those out.

When it comes to SSD storage, leaving 20% unused can drastically increase the life-time of the storage. That may not be a consideration. IDK.  For me, it is, so I don't allocate anywhere near the full size of the SSD.

Snapshots and the way that LVs can be expanded while actively being used, if the VG has free space, are what make LVM so very useful.  Unlike the other advanced volume managers available in Linux, LVM has been enterprise ready over 20 yrs.  

If you don't plan to use those features _and_ don't mind downtime due to storage reconfiguration, then you'll find simple partitioning and file systems much easier to grasp.

---

