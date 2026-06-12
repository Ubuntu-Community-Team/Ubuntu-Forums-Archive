---
title: "Adding new HDD - No UUID"
date: 2024-02-05
forum: Server Platforms
---

### Post by scottbouch-com on 2024-02-05
Hi all,

I have added two new 6TB drives to my HP Proliant server, using the HP smart array to form a Raid 1 volume.

I have tried to create a partition table and partition using parted:

```

(parted) mklabel gpt
Warning: The existing disk label on /dev/sdg will be destroyed and all data on this disk will be lost. Do you want to
continue?
Yes/No? y                                                                 
(parted) unit TB                                                          
(parted) mkpart                                                           
Partition name?  []? primary                                              
File system type?  [ext2]? ext4                                           
Start? 0%                                                                 
End? 100%                                                                 
(parted) print                                                            
Model: HP LOGICAL VOLUME (scsi)
Disk /dev/sdg: 6.00TB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name     Flags
 1      0.00TB  6.00TB  6.00TB  ext4         primary

(parted) quit                                                             
Information: You may need to update /etc/fstab.

```

I used ls to find the UUID of the new partition (sdg1):

```

$ ls -l /dev/disk/by-partuuid
total 0
...
lrwxrwxrwx 1 root root 10 Feb  5 23:53 76dcf6fb-cc36-4160-9b17-7e06dd401c5d -> ../../sdg1
...

```

I added the UUID to fstab:

```

# Backup 6TB slots 10, 11:
UUID="76dcf6fb-cc36-4160-9b17-7e06dd401c5d" /mnt/backup ext4 defaults 0 0 0

```

But then...

```

$ sudo mount -a
mount: /mnt/backup: can't find UUID="76dcf6fb-cc36-4160-9b17-7e06dd401c5d".

```

So, I poke around:

```

$ sudo fdisk -l
.....
Disk /dev/sdg: 5.46 TiB, 6001141571584 bytes, 11720979632 sectors
Disk model: LOGICAL VOLUME  
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: A7DFA896-1091-4BCB-BBE8-3BE85363BDA3

Device     Start         End     Sectors  Size Type
/dev/sdg1   2048 11720978431 11720976384  5.5T Linux filesystem

```

And ls returns no /dev/sdg:

```

$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 Feb  5 23:45 10ad5270-3d25-4c57-a5c4-6069d3a9c74f -> ../../sdd1
lrwxrwxrwx 1 root root 10 Feb  5 23:44 1d11eb02-7f1a-475b-adfe-7adb47195e53 -> ../../sdc1
lrwxrwxrwx 1 root root  9 Feb  5 23:45 67f783ae-26b9-43dd-9d16-7df57a1bd717 -> ../../sde
lrwxrwxrwx 1 root root  9 Feb  5 23:44 9463c401-f5ea-4954-ae8d-77397080623c -> ../../sdb
lrwxrwxrwx 1 root root 10 Feb  5 23:48 d60bea07-e2ab-4c15-b1ae-b7d0b5abb5a7 -> ../../sdf1
lrwxrwxrwx 1 root root 10 Feb  5 23:44 e42610e5-a21b-4d73-87c8-2102fdc6d021 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb  5 23:48 eefc7083-1481-4ef6-9150-3ac138b05f50 -> ../../dm-0

```

However, we do have a partition UUID for sdg1:

```

scott@hal:~$ ls -l /dev/disk/by-partuuid
total 0
lrwxrwxrwx 1 root root 10 Feb  5 23:44 30290225-ccb9-41c9-89d3-64007eb8f66f -> ../../sdc1
lrwxrwxrwx 1 root root 10 Feb  5 23:44 34a98511-ded7-439f-9dad-21c99b056b45 -> ../../sda2
lrwxrwxrwx 1 root root 10 Feb  5 23:44 3b242c84-5dd0-47d4-ace5-0f6e4aba10cc -> ../../sda1
lrwxrwxrwx 1 root root 10 Feb  5 23:53 76dcf6fb-cc36-4160-9b17-7e06dd401c5d -> ../../sdg1
lrwxrwxrwx 1 root root 10 Feb  5 23:44 7b8f192e-2b0a-4636-aab6-d14976ad26be -> ../../sda3

```

It strikes me as a little strange to have a partition but no disk UUID

A final check with lsblk shows no information against sdg or sdg1:

```

lsblk -f
......
NAME                    FSTYPE      FSVER    LABEL UUID                                   FSAVAIL FSUSE% MOUNTPOINTS
sdb                     ext4        1.0      Store 9463c401-f5ea-4954-ae8d-77397080623c      7.8G    95% /mnt/store
sdc                                                                                                      
&#9492;&#9472;sdc1                  ext4        1.0      CCTV  1d11eb02-7f1a-475b-adfe-7adb47195e53       23G    92% /mnt/cctv
sdd                                                                                                      
&#9492;&#9472;sdd1                  ext4        1.0      Files 10ad5270-3d25-4c57-a5c4-6069d3a9c74f     96.6G    74% /mnt/files
sde                     ext4        1.0            67f783ae-26b9-43dd-9d16-7df57a1bd717                  
sdf                                                                                                      
&#9492;&#9472;sdf1                  ext4        1.0            d60bea07-e2ab-4c15-b1ae-b7d0b5abb5a7      844G     3% /var/www/html
sdg                                                                                                      
&#9492;&#9472;sdg1

```

Any ideas on what I've done wrong?

There is no data on the volume, so happy to try re-formatting it again.

Cheers, Scott

---

### Post by TheFu on 2024-02-05
Always put RAID inside a partition.
Never use the whole disk for RAID.
There are reasons that you can look up to understand why.

Looks like sdb and sde are already screwed.

---

### Post by MAFoElffen on 2024-02-05
For hardware RAID... Using HP SMART-ARRAY card right? That is okay without putting (hardware) RAID inside of a partition... only because hardware RAID cards do not understand how to do that. (I will bring this back up at the end...)

But if you were doing software RAID mdadm, LVM2, ZFS... Even though it is possible to create then as whole disk... Bad idea, and many perspective problems down the road. Always put those within a partition with a partition table. 

On what you are doing... Misunderstanding of what to use in fstab.
Wrong UUID. For fstab you use the UUID of the Filesystem, not the Partition UUID...

Programmatically... Example for my /dev/sdc1. Here is 3 ways to retrieve the UUID:
```

mafoelffen@Mikes-ThinkPad-T520:~/Scripts$ lsblk -r -o uuid /dev/sdc | grep -v 'UUID\|^$'
9539864118717640029
mafoelffen@Mikes-ThinkPad-T520:~/Scripts$ sudo blkid -s UUID -o value /dev/sdc1
9539864118717640029
mafoelffen@Mikes-ThinkPad-T520:~/Scripts$ ls -l /dev/disk/by-uuid | awk '/sdc1/ {print $9}'
9539864118717640029

```
I set any of these ways to a variable called UUID, then echo that i the fstab file line. For example
```

sudo echo -e "UUID=$(sudo blkid -s UUID -o value /dev/sdc1) /data ext4 defaults 0 0" >> fstab

```
Why? Because I am getting old and don't always trust myself to transcribe a long string of numbers... And a lot easier for me. i don't even have to look at it, and I know it will be correct.

[HR][/HR]
Back to hardware RAID. Is this commercial or for private use? If commercial/production, then you are just following within your boundaries, policies, and directives made from decisions above you... But it puts you in a box with set limitations. I can not talk for TheFU, but both of us came from the production world... Where we had to follow what we were directed to...

But that was decades ago. Circa about the 90's though 2010. Decades old tech and methodologies. The original reason for hardware RAID first was to put together disks, into a larger group. The for speed from striping. Then for redundancy from the striping or speed from RAID10, RAID50, RAID60. But when things went wrong, to reassemble RAID takes a long time, with conflicts when your mission is uptime. It is also very stringent on what it can do = not very flexible.

I went from there on servers, to doing jbod or if the controllers didn't do jbod, then tricking them by passing through the disks through the HBA RAID Controller as a collection of single-disk RAID0... So I could do software RAID mdadm. More flexible. Can adapt. But still long downtime when something went wrong. 

So about 2010 to 2012... LVM2. Can change and adapt while live/online. Used it with it's internal RAID capabilities... and without. Can do snapshots. Can add disks, and grow while online. A little ramp up to learn and et productive, but not bad. TheFu can back me on it's merits.

2014 to 2016, went back to ZFS. Very adaptable and portable. Can migrate pieces very easily. Snapshots. Send/Receive for Backups. RAID can rebuild, grow and transform online/live. Can add, remove, change disks online, live. Very steep ramp up/learning curve.

Currently, these days, I recommend and prefer LVM2 and ZFS. Both can grow with you, and not leave you in a dead-end. Both make change and migrations easy.

If for personal use... Your choices.

---

### Post by scottbouch-com on 2024-02-06
Hi guys,  thank you for the contributions so far.


***Background:***

I perhaps should have said, I'm just a hobbyist at home trying to learn about Linux and programming, and a fan of open source projects. I'm an engineer but don't work in IT or computing, I presently work on developing renewable energy projects.

I bought the server-second hand as old corporate equipment, and it runs in my garage. The server just runs Zoneminder CCTV, Emby media server and simple web pages for me and my family members via my home broadband connection.

This new 6TB volume is intended as a remote back-up of our Synology NAS, which is used for family photos, kids school work, etc.. (hence the mnt/backup mount point)

I only have the opportunity to add drives and mess with fstab on a very rare occasion (ie: when a drive fails or I need to do a total rebuild) so I'm in no way experienced or know good practice with this. Each time I just have to head to the internet looking for guides to help me along, and clearly I can miss important details by not being "in the know". I also don't have any friends who know Linux, so can't invite anyone round for a cup of tea and some assistance and/or training.


***Likely Solutions:***

When **TheFu** said "Looks like sdb and sde are already screwed." - is this something I've caused with this new volume? Do you say that as lsblk shows no sdb1 or sde1 partitions? I'm a bit worried now. I didn't know one volume could mess up another.
- sdb: I can still access the files in (mnt/store) so hopefully it's not ruined or partially corrupted. Interestingly when I added this volume to fstab, I used the disk UUID as shown by ls "-l /dev/disk/by-uuid" - this is not out of personal preference or any guidance, it's just down to stumbling my way through internet guides and trying my best.
- sde: This is just a hangover from a change I made a while ago - it's a drive I had previously mounted elsewhere but is now redundant, just still sat in the bay, unused, please ignore.

When I used "parted" for the new volume, I should have specified perhaps 1% to 99% ?

Fstab - Should I use the drive UUID, not the partition UUID? (not relevant to me now, but what happens when a drive had two partitions?)

Please where possible point me at idiots-guide type explanations as I'm a a fair novice here just having a go at providing solutions for family file storage, and hoping to learn something on the way.

Is it worth me just re-running "parted" with the smaller 1% to 99% specified? I'm not sure about how to specify the LVM/ZFS options with "parted" as suggested by **MaFoElffen** , does this replace where I used "Partition name?  []? primary" ?

Many thanks again, Scott.

---

### Post by scottbouch-com on 2024-02-06
I just went ahead and tried parted again with 1% and 99% for sdg:

```

~$ sudo parted /dev/sdg
[sudo] password for scott: 
Sorry, try again.
[sudo] password for scott: 
GNU Parted 3.4
Using /dev/sdg
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) mklabel gpt                                                      
Warning: The existing disk label on /dev/sdg will be destroyed and all data on this disk will be lost. Do you want to
continue?
Yes/No? y                                                                 
(parted) unit TB                                                          
(parted) mkpart                                                           
Partition name?  []? primary                                              
File system type?  [ext2]? ext4                                           
Start? 1%                                                                 
End? 99%                                                                  
(parted) print                                                            
Model: HP LOGICAL VOLUME (scsi)
Disk /dev/sdg: 6.00TB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name     Flags
 1      0.06TB  5.94TB  5.88TB  ext4         primary

(parted) ^C                                                               

Information: You may need to update /etc/fstab.


```


But still no UUID for the drive or partition..... (scroll down code for sdg and sdg1)

```

$ lsblk -f
NAME                    FSTYPE      FSVER    LABEL UUID                                   FSAVAIL FSUSE% MOUNTPOINTS
loop0                   squashfs    4.0                                                         0   100% /snap/certbot/3566
loop1                   squashfs    4.0                                                         0   100% /snap/certbot/3462
loop2                   squashfs    4.0                                                         0   100% /snap/core/16091
loop3                   squashfs    4.0                                                         0   100% /snap/core/16202
loop4                   squashfs    4.0                                                         0   100% /snap/core18/2812
loop5                   squashfs    4.0                                                         0   100% /snap/core18/2796
loop6                   squashfs    4.0                                                         0   100% /snap/core20/2015
loop7                   squashfs    4.0                                                         0   100% /snap/core20/2105
loop8                   squashfs    4.0                                                         0   100% /snap/lxd/23991
loop9                   squashfs    4.0                                                         0   100% /snap/lxd/24061
loop10                  squashfs    4.0                                                         0   100% /snap/snapd/20290
loop11                  squashfs    4.0                                                         0   100% /snap/snapd/20671
sda                                                                                                      
&#9500;&#9472;sda1                                                                                                   
&#9500;&#9472;sda2                  ext4        1.0            e42610e5-a21b-4d73-87c8-2102fdc6d021    655.3M    26% /boot
&#9492;&#9472;sda3                  LVM2_member LVM2 001       erIPHA-0oax-yLOM-QO94-NP1D-Ckp2-6VRuBE                
  &#9492;&#9472;ubuntu--vg-ubuntu--lv
                        ext4        1.0            eefc7083-1481-4ef6-9150-3ac138b05f50     78.7G    26% /
sdb                     ext4        1.0      Store 9463c401-f5ea-4954-ae8d-77397080623c      7.8G    95% /mnt/store
sdc                                                                                                      
&#9492;&#9472;sdc1                  ext4        1.0      CCTV  1d11eb02-7f1a-475b-adfe-7adb47195e53       23G    92% /mnt/cctv
sdd                                                                                                      
&#9492;&#9472;sdd1                  ext4        1.0      Files 10ad5270-3d25-4c57-a5c4-6069d3a9c74f     96.6G    74% /mnt/files
sde                     ext4        1.0            67f783ae-26b9-43dd-9d16-7df57a1bd717                  
sdf                                                                                                      
&#9492;&#9472;sdf1                  ext4        1.0            d60bea07-e2ab-4c15-b1ae-b7d0b5abb5a7      844G     3% /var/www/html
sdg                                                                                                      
&#9492;&#9472;sdg1 
```

Can anyone spot what I'm doing wrong please?

Thanks, Scott

---

### Post by MAFoElffen on 2024-02-06
You partitoned it, but did not format it with a filesystem yet... So no UUID returns for that filesystem ,because it doesn't exist yet. (Please- Reread my post.)
```

sudo mkfs -t ext4 /dev/sdg1
lsblk -f /dev/sdg

```

---

### Post by TheFu on 2024-02-06
> **scottbouch-com said:**
> 
I perhaps should have said, I'm just a hobbyist at home trying to learn about Linux and programming, and a fan of open source projects. I'm an engineer but don't work in IT or computing, I presently work on developing renewable energy projects.


I trained as an ASE, but my first "real job" was coding flight control systems for one-of-a-kind equipment.  The company of 22K people didn't have any "IT" department that we knew about.  We sourced equipment and did all upgrades from PCs to microwave links to 10base2 coax runs.  After about 7 yrs working semi-close to my degree, I moved fully into computing and software.

> **scottbouch-com said:**
> 
I bought the server-second hand as old corporate equipment, and it runs in my garage. The server just runs Zoneminder CCTV, Emby media server and simple web pages for me and my family members via my home broadband connection.

I remember thinking that I needed "server hardware" for stuff.  Turns out it is better, cheaper, more flexible, and more efficient to have 2 cheapo desktops for any required redundancy.  My garage isn't suitable for any computers. It gets much too cold and much too hot.  With SSDs, failures are pretty rare, so doing RAID really isn't necessary.  I spoke to a guy that sells SSD-based RAID systems.  He said that servers are replaced faster than the SSDs wear out, so it is really only needed by dinosaurs who insist based on their old ideas of storage failures.  He didn't mind selling them 2x the storage, even if it wasn't needed.  I have some RAID HDDs, but those are nearly retired now. I used to run virtual machines on RAID until about 3-4 yrs ago when I moved all the VMs to quality SSD storage.

I have nightly, automatic, backups.  Should nearly any of my storage fail, it will be an inconvenience, not a bad day.  RAID never has and never will replace the need for backups.  Backups solve 1000 problems, including corrupted RAID arrays.  RAID, OTOH, solves 2 issues. HA and, perhaps, slightly better performance, provided a quality HW-RAID HBA is used.  For nearly any purpose, RAID is a complexity that isn't needed.  If you are in an industry where losing a transaction isn't allowed, you'll have RAID and you'll write every transaction synchronously to 2 geographically dispersed DB servers.  I've designed systems like that and we deployed them.  OTOH, if the company can accept a 20-30 second delay in having transactional redundancy, tremendous performance improvements and cost systems are possible with a delayed replication method handled by the DBMS.

> **scottbouch-com said:**
> 
This new 6TB volume is intended as a remote back-up of our Synology NAS, which is used for family photos, kids school work, etc.. (hence the mnt/backup mount point)

I'm always surprised when people want RAID for backups.  We did it in a corporate environment, but everyone laughed a bit about doing it. This was due to some cheaper enterprise SAN storage that was RAID5 or RAID1 and that was it.  Backups to it were put on the RAID5 area.  None of my projects used that SAN storage. We used higher end SAN frames and did BCVs for backups completely outside the servers.  The BCVs were mapped to primary storage seen by the servers, but cloning each of those disks happened inside the storage frame and the backup servers would mount the BCSs read-only to push to tape. Further, we'd use the SAN ability to clone the BCVs over the backup WAN to a different location about 500 miles away for disaster recovery purposes.  BCVs aren't something most people know about. Very much an enterprise storage architecture ($$$$$).

> **scottbouch-com said:**
> 
I only have the opportunity to add drives and mess with fstab on a very rare occasion (ie: when a drive fails or I need to do a total rebuild) so I'm in no way experienced or know good practice with this. Each time I just have to head to the internet looking for guides to help me along, and clearly I can miss important details by not being "in the know". I also don't have any friends who know Linux, so can't invite anyone round for a cup of tea and some assistance and/or training.


That's not a bad thing.  Storage that works is good.  You should look into joining a LUG - Linux User Group - where you can get live guidance to fill in gaps, ask questions, get lots of different perspectives.  It is always best to learn from someone else's mistakes, so you can avoid them.

> **scottbouch-com said:**
> 
***Likely Solutions:***

When **TheFu** said "Looks like sdb and sde are already screwed." - is this something I've caused with this new volume? Do you say that as lsblk shows no sdb1 or sde1 partitions? I'm a bit worried now. I didn't know one volume could mess up another.
- sdb: I can still access the files in (mnt/store) so hopefully it's not ruined or partially corrupted. Interestingly when I added this volume to fstab, I used the disk UUID as shown by ls "-l /dev/disk/by-uuid" - this is not out of personal preference or any guidance, it's just down to stumbling my way through internet guides and trying my best.
- sde: This is just a hangover from a change I made a while ago - it's a drive I had previously mounted elsewhere but is now redundant, just still sat in the bay, unused, please ignore.


I made some assumptions.  Recovery tools don't like to work on storage devices that don't have partitions.  Also, storage without partitions means it doesn't have labels which can be used to toggle your memory for what data is actually stored on the physical disk.  The idea of using HW-RAID cards in a home environment isn't really a good idea.  If that HBA fails, you'll likely need an exact replacement to gain access to the data.  If your setup is using "Fake-RAID", you have a similar issue with replacing the motherboard for an nearly exact replacement AND you have the problem that Fake-RAID never includes the chips that make RAID performance better than SW-RAID.
OTOH, SW-RAID is extremely flexible. I've migrated my SW-RAID between 4 different system, changing motherboards and CPU architectures each time.  Performance of SW-RAID used to be terrible, but as CPUs and SATA/SAS has gotten faster, that issue is basically done.

Anyway, in a home environment, I can't see any good reason for RAID anymore.  RAID performance is completely destroyed by NVMe storage and it is highly unlikely anyone has anything so critical to need more than a few hundred GB ... which will easily fit on a 1TB NVMe device costing less than $55.  I'm not just saying it.  I follow this:
```
NAME                                TYPE FSTYPE        SIZE FSAVAIL FSUSE% LABEL      MOUNTPOINT
nvme0n1                             disk             465.8G                           
&#9500;&#9472;nvme0n1p1                         part vfat           50M   43.2M    12% EFI        /boot/efi
&#9500;&#9472;nvme0n1p2                         part ext4          600M  250.8M    49% boot       /boot
&#9492;&#9472;nvme0n1p3                         part LVM2_member   465G                           
  &#9500;&#9472;vg00-swap                       lvm  swap          4.1G                           [SWAP]
  &#9500;&#9472;vg00-root--00                   lvm  ext4           35G    4.4G    82% root       /
  &#9500;&#9472;vg00-var                        lvm  ext4           55G     36G    28% var        /var
  &#9500;&#9472;vg00-home                       lvm  ext4           26G   14.4G    38% home       /home
  &#9500;&#9472;vg00-ubuntu2204--srv            lvm                 15G                           
  &#9500;&#9472;vg00-ubuntu22.04--srv--2        lvm                 15G                           
  &#9500;&#9472;vg00-Mint21.1                   lvm  zfs_member     40G                rpool      
  &#9500;&#9472;vg00-lxd                        lvm  zfs_member     50G                lxd        
  &#9500;&#9472;vg00-lv--vpn09--2004            lvm                7.5G                           
  &#9500;&#9472;vg00-lv--blog44                 lvm               30.2G                           
  &#9500;&#9472;vg00-lv--xen41--1804            lvm               12.5G                           
  &#9500;&#9472;vg00-lv--zcs45--1804            lvm                 35G                           
  &#9492;&#9472;vg00-lv--tv                     lvm  ext4          100G   50.5G    43%            /TV
```
That's an NVMe device with 6 virtual machines and 10 lxc containers on it. None is using RAID.  My backup storage is a spinning 8TB HDD with a 5 yr warranty. It is split into 2 logical volumes.  I'm careful to assign entire disks for primary or backup storage use.  When storage fails, it doesn't care about partitions.

My storage architecture method has primary and backup storage as the main considerations.  I try to keep it really simple.  None of my storage file systems are larger than 4TB.  About a decade ago, I was buying 4TB HDDs, so it made sense to place a 4TB limit.  Smaller partitions can be backed up into 4TB file systems.  Larger disks can be split into 4TB chunks.  Additionally, my primary storage is never USB connected outside sneaker*net uses.  USB storage that is connected most of the time is for backups, never primary.  Primary storage is NVMe, SAS, SATA, eSATA, or Infiniband connected.  I've been burned by USB connectors becoming lose far too often to trust it.

> **scottbouch-com said:**
> 
When I used "parted" for the new volume, I should have specified perhaps 1% to 99% ?

What's a "volume" in this case?  If this isn't connected to a HW-RAID HBA and being used in HW-RAID mode, then you should have
[LIST=1]
[*]Created a new GPT partition table
[*]Created at least 1 primary partition
[*]Then, you have a choice - to LVM or not.  I'm assuming you won't bother with RAID anymore.
[*]If you don't use LVM, you'll want to decide how large the partitions should be for the storage.  This is hard and nobody ever gets it correct.  In 30 yrs, I've never guessed correctly.
[*]If you DO use LVM, then you'll create PV on the 1 partition, assign the full PV to a VG, then create 1 or more LVs inside the VG sized for the amount of storage you know you'll use in the next 1-2 months only.  Also, you'll want to leave as much of the VG unassigned as possible for future flexibility.  LVs can be expanded easily. Reducing an LV is a hassle, but less than reducing a partition.  Above, all that storage output that starts with vg00 .... vg00 is the VG on my NVMe storage.  The name after that is the LV name. Each is sized to be the size I thought I'd need.  To extend the life of the SSD, I try to never use more than 80% of the total storage.  I also try to leave sufficient empty space in the VG to allow snapshots for my backup needs.  This is one of the main reasons to use LVM, besides the added flexibility and trivial resizing.  Increasing the size of any LV is just 1 command and about 5 seconds.
[*]So, now you have either partition(s) with or without LVs.  You need to place a file system which can be mounted and while you are at it, give each file system a unique label.  LVM prefers if you use ext4 and many commands work with ext4 best.  If you don't have a specific reason to use some other file system, choose ext4.
[/LIST]

> **scottbouch-com said:**
> 
Fstab - Should I use the drive UUID, not the partition UUID? (not relevant to me now, but what happens when a drive had two partitions?)

Actually, I mount using the LVM VG and LV names.  If I don't use LVM, I'll use the "LABEL=" method to mount.
Example VG+LV fstab mounts:
```
/dev/vg00/root-00                          /         ext4 defaults 0 1
/dev/vg00/home                             /home     ext4 defaults 0 1
/dev/vg00/var                              /var      ext4 defaults 0 1
/dev/vg00/swap                             none      swap sw 0 0

```
Example LABEL fstab mount:
```
LABEL=RAID1-Array              /raid1-old          ext4 noatime,nofail,errors=remount-ro  0  2
LABEL=R2-Array                 /raid2-old          ext4 noatime,nofail,errors=remount-ro  0  2
```

> **scottbouch-com said:**
> 
Please where possible point me at idiots-guide type explanations as I'm a a fair novice here just having a go at providing solutions for family file storage, and hoping to learn something on the way.
Much of this isn't written down anywhere. It is learned through mentoring or failures.  Things change faster than books can keep up.  Things that were valid in 1995 or 2005 have been completely invalidated as the hardware has changed completely.  For example, the idea about sizing swap used to be 2-3x the amount of physical RAM.  That was when 32MB of RAM and 4GB HDDs were huge.  There is such a thing as too much swap.  The purpose of swap has changed over the decades.  These days, we mainly want to use it as a way to get feedback about RAM exhaustion coming.  We want swapping to happen to make us "feel" the system becoming slow. RAM is cheap.  Only really limited budgets shouldn't have more RAM than needed in their systems.  It is common for "server HW" to have 128-256GB RAM, desktops to have 32G-64G. My "VM+LXC Server" has 32G of RAM - 2GB is taken by the iGPU:
```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:           30Gi        21Gi       2.1Gi       134Mi       7.5Gi       9.1Gi
Swap:         4.1Gi       947Mi       3.2Gi
```
Even with all those VMs and containers running, there's about 10G free.  I have a nearly identical system next to it.  Barely doing anything.  Eventually, I'll migrate 10% of the VMs and containers to it:
```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:           30Gi       1.5Gi       5.1Gi        12Mi        24Gi        28Gi
Swap:         4.1Gi       5.0Mi       4.1Gi
```

These systems use about 65W when not working hard each. They both have 8 HDDs connected.  They were both upgrades. Due to timing of the purchase for the parts, one was about $230 and the other was $430.  Not high-end systems at all, just 6-cores, but nearly 20K passmarks, if you want to compare system performance.

> **scottbouch-com said:**
> 
Is it worth me just re-running "parted" with the smaller 1% to 99% specified? I'm not sure about how to specify the LVM/ZFS options with "parted" as suggested by **MaFoElffen** , does this replace where I used "Partition name?  []? primary" ?

There are LVM tutorials out there. Good news is that LVM is LVM is LVM.  A tutorial for ubuntu or debian or rhel will all be the same.  LVM is a "volume manager". The file systems are different.  LVM is modeled after Veritas VM, which means that any Unix admin knows the ideas already.  HP, AIX, Solaris, Irix, DEC (bought by HP) people all know these things.

ZFS is a volume manager AND file system in one.  In many ways, it is easier, but it isn't trivial to use without working through a number of tutorials and getting familiar.  I've been using ZFS on one of my systems for about year now.  Initially, I worked through a tutorial and setup some user storage areas.  If anything bad happens, I doubt I could recover though ZFS tools.  I'd likely wipe the system, start over and restore from my backups.  My backups work at a level that the storage methods (partitions, LVM, ZFS) don't matter.

I've been using ZFS for container storage for about 3-4 yrs.  Fortunately, I haven't needed to know much.  Here's my nextcloud server container storage:
```
 Filesystem                             Type  Size  Used Avail Use% Mounted on
lxd/containers/nextcloud-lxd           **zfs**    40G   11G   29G  28% /
/dev/mapper/WDBLK_8T-lv_d7             ext4  3.6T  1.1T  2.4T  32% /media/Music
hadar:/d/rom/export/www/vhosts/gallery nfs   196G  120G   67G  65% /media/Photos
/dev/mapper/istar--vg-lv_media         ext4  3.5T  3.5T   31G 100% /media/ebooks
```
The last 3 areas are outside the container, but passed into the nextcloud system using container tools. See ... nothing in the fstab at all.
```
$ more /etc/fstab 
# UNCONFIGURED FSTAB FOR BASE SYSTEM

```
The 40G size of the ZFS is shared across all the linux containers on that system.  Even so, 29G is unused. Guess I sized it too large.

---

### Post by scottbouch-com on 2024-02-06
> **MAFoElffen said:**
> You partitoned it, but did not format it with a filesystem yet... So no UUID returns for that filesystem ,because it doesn't exist yet. (Please- Reread my post.)
```

sudo mkfs -t ext4 /dev/sdg1
lsblk -f /dev/sdg

```

That "aced" it, thank you!!!! Just one command missed.

I'll digest all the thoughts in this thread about the need for raid vs SSD's etc... There is a wealth of good information here, thank you to you both!!

The drive is now mounted perfectly, thank you. Now to look into rsync and alternatives to back up the NAS to this drive.

Thank you again.

---

### Post by TheFu on 2024-02-06
You need to start any partition on a sector boundary.  1MB is unit for the start.  Don't use percentages.

Also, If you aren't using LVM, I wouldn't create a single, huge, partition.  What size are the files you plan to backup?

As for backups - rsync isn't the best backup solution. Use something that does versioning like rdiff-backup.  Rdiff-backup and rsync commands are very similar, but you get more efficient backups with versioning, which is important.  The only time I prefer rsync over rdiff-backup is with media files (music/audiobooks/video files).  For all other files, I want versioning.

---

