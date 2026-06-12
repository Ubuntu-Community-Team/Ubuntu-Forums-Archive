---
title: "How to setup a backup system similar to OSX Time-Machine based on BTRFS"
date: 2022-01-24
forum: Tutorials
---

### Post by bruzzlee-ch on 2022-01-24
**Introduction**
Spoiled by the OSX Time Machine solution I've been using for many years, I was looking for a similar backup method after switching completely to Kubuntu.
 My first approach was to use "Back-In-Time" which worked great and did exactly what I needed.
                             "Back-In-Time" is basically a GUI interface to automate rsync commands and provides a good overview over all the snapshots/backups.
 Over time, the complexity and volume of data grew to the point where each "back-in-time" (incremental) backup took about an hour.

 It was time to investigate in a new solution.
  
 This guide is intended to help set up a performant backup solution that takes advantage of the "copy on write" technology of BTR file systems.
This should be a "simple" tutorial with examples covering the topics of how to set up an automated BTRFS snapshot/backup configuration, similar to OSX Time-Machine with excluded subfolders. (Without GUI)
Please let me know if you have any suggestions or questions about this tutorial.

 **Quick objective speed comparison ** 
 Amount of changes ~100 MB:
[LIST]
[*]Time needed for snapshots with "Back-In-Time": ~60 Minutes 
[*]Time needed for snapshots with "BTRBK": <1 Minute 
[/LIST]

 **Initial ****setup**
   
[LIST]
[*] Kubuntu (EFI boot) installed on a *SYSTEM* SSD on EXT4 LVM2  (250 GB) 
[*]*DATA *HDD (2 TB) 
[*]*BACKUP* HDD (3 TB) 
[*]Windows SSD (150 GB) 
[/LIST]
Names written in "Italic" are used late ron in the tutorial

**Goal**
Take incremental snapshots of:
 
[LIST]
[*]Root     system of Kubuntu 
[*]Home     folder (Kubuntu) 
[*]DATA     HDD (exuding specific folders) 
[/LIST]
  
  **Steps to setup BTRFS on data disks (Essential if you are coming from EXT4 partitions)**                            
[LIST=1]
[*]Make     sure you have a separate backup of all your data on a separate     drive in case anything goes wrong
[LIST=1]
[*]```
rsync -a --recursive --info=progress2 /media/UserData/ /media/USB_BackupUserData/
``` 
[*]Add ```
--exclude=XYZ
``` to exclude folders like Downloads etc. which you don't want to back up 
[/LIST]
  
[*]     Convert your file systems (DATA and BACKUP) to BTRFS if they are not already.
[LIST=1]
[*]```
btrfs-convert /dev/sda1 
``` will convert an ext4 partition to btrfs 
[/LIST]
  
[*]"Move"     all your data on the DATA HDD root into a subvolume     called @
```
btrfs subvolume snapshot /media/UserData/ /media/UserData/@
``` 
[*]Delete original "file references" from the root of the HDD 
-xdev is critical! It defines that it only deletes files in the current mounted device (snapshot)
```
find /media/UserData -xdev -delete
``` 
[*]Edit /etc/fstab
[LIST=1]
[*]     Mount @ as your "normal" data volume 
[*]     Mount DATA HDD as a root mounting point 
[*]Mount BACKUP HDD as a root mounting point
```
[FONT=monospace][COLOR=#000000]UUID=[/COLOR][/FONT][FONT=monospace][COLOR=#000000][FONT=monospace]XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX[/FONT]  /media/UserData_root        btrfs    defaults,subvol=/                     0       1[/COLOR][/FONT][FONT=monospace]
UUID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX  /media/UserData             btrfs    defaults,subvol=@                     0       1 
UUID=YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY  /media/Backup               btrfs    defaults                              0       1[/FONT]
``` 
[/LIST]
             
[/LIST]

[LIST=1]
[*]Create a folder on DATA called snapshots 
[*]     Create a folder on BACKUP called something like btr_backup_data 
[*]     On @ "convert" every folder which should be _excluded_ from     the backup into a subvolume.
Nested Subvolumes will be ignored during a snapshot of the parent subvolume.
```
cd /media/UserData
mv Downloads/ Downloads_old
btrfs subvolume create Downloads
cp -ax --reflink=always /media/UserData/Downloads_old/. /media/UserData/Downloads
rm -rf /media/UserData/Downloads_old

``` 
[*]     Add COW-off attribute to folders which should have COW off     (optional) 
[https://wiki.archlinux.org/title/Btrfs#Disabling_CoW](https://wiki.archlinux.org/title/Btrfs#Disabling_CoW)
```
chattr -R +C /media/UserData/Downloads
``` 
[/LIST]

**Automate backup with BTRBK**

[LIST=1]
[*]Install btrbk
[https://github.com/digint/btrbk](https://github.com/digint/btrbk)
```
sudo apt-get update -y
sudo apt-get install -y btrbk
``` 
[*]Edit /etc/btrbk/btrbk.conf
The following configuration will lead to a daily snapshot which will be kept for 200 days.  The first snapshot of each month will be kept 30 months. 
Each month, a snapshot of the subvolume VirtualBoxVMs will be taken and saved forever.
Don't preserve snapshots on original disk >1 day (latest).
```
# Enable transaction log
transaction_log            /var/log/btrbk.log

# Use long timestamp format (includes hour/minute)
timestamp_format           long
 
snapshot_preserve_min  latest
snapshot_preserve      no

# Create snapshots only if the backup disk is attached
#snapshot_create ondemand

target_preserve_min    no
target_preserve        200d 30m

snapshot_dir           btrbk_snapshots

[FONT=monospace][COLOR=#000000]volume /media/UserData_root [/COLOR]
  target send-receive /media/Backup/btr_backup_UserData 
    subvolume @ 
      target_preserve 200d 30m 
    subvolume @/VirtualBoxVMs 
      target_preserve    *m[/FONT]

``` 
The config can be tested by executing a dry run of btrbk
```
sudo btrbk -v -n run
``` 
[*]Create script [FONT=monospace][COLOR=#000000]/etc/btrbk.daily/btrfs_backup.sh
T[/COLOR][/FONT]his file will be executed with root privileges. Make sure it is only accessible by superusers.
```
[FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]#!/bin/sh -e[/COLOR][/FONT][/COLOR][/FONT]
[FONT=monospace][COLOR=#000000][FONT=monospace][FONT=monospace][COLOR=#000000]btrbk -q run[/COLOR]
[/FONT][/FONT][/COLOR][/FONT]
``` 
[*][FONT=monospace][COLOR=#000000]Install anacron[/COLOR][/FONT] 
[*][FONT=monospace][COLOR=#000000]Add following line to /etc/anacrontab 
The script will be executed daily 10 minutes after boot.[/COLOR][/FONT]
```
[FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]1       10      btrbk.daily     /bin/bash /etc/btrbk.daily/btrfs_backup.sh[/COLOR][/FONT][/COLOR][/FONT]
``` 
[/LIST]

**Steps to setup BTRFS for System disks (Optional)** 
[LIST=1]
[*]Basically you can follow this guide to convert an existing Ubuntu installation: [https://www.howtoforge.com/how-to-convert-an-ext3-ext4-root-file-system-to-btrfs-on-ubuntu-12.10-p2](https://www.howtoforge.com/how-to-convert-an-ext3-ext4-root-file-system-to-btrfs-on-ubuntu-12.10-p2) 
[*]LVM2  systems users need to mount the LVM2 mapper point  e.g.  ```
/dev/mapper/vgkubuntu-root
``` instead of   ```
/dev/sda1
``` 
[/LIST]


**Add System disks to automated backup ****(Optional)**
[LIST=1]
[*]Edit /etc/btrbk/btrbk.conf
Add the following lines to enable backups for the system and home subvolume.
In addition, this config will create a snapshot of the root and home subvolume each day. Daily snapshots are kept for 30 days and monthly for 10 months.
```
[FONT=monospace]
volume /media/System_root 
  target send-receive /media/Backup/btr_backup_System 
    subvolume @ 
      target_preserve  30d 10m 
    subvolume @home 
      target_preserve   30d 10m 
[/FONT]
``` 
[/LIST]

[B]Steps to set up non BTRFS disk backups (Optional)
[/B]If a backup is needed of a non BTRFS partition (e.g. NTFS) then the data needs to be copied (synced) to a BTRFS partition previous to a snapshot.
In the following example, a Windows user folder is backed up on a BTRFS system.
Adding rsync commands will lead to an increase of the overall backup process time.

[LIST=1]
[*]Mount the NTFS partition by editing /etc/fstab
```
[FONT=monospace][COLOR=#000000]UUID=ZZZZZZZZZZZZZZZZ                      /media/Windows              ntfs     defaults,nls=utf8,umask=007,gid=46    0       0[/COLOR][/FONT]
``` 
[*]Create a folder and subvolume on the backup disk where the data is synced to
```
mkdir /media/Backup/btr_backup_Windows
 btrfs subvolume create /media/Backup/btr_backup_Windows/sync
``` 
[*]edit [FONT=monospace][COLOR=#000000]/etc/btrbk.daily/btrfs_backup.sh [/COLOR]
[/FONT]```
[FONT=monospace][COLOR=#000000]#!/bin/sh -e [/COLOR]
rsync -az --delete \ 
      --inplace --numeric-ids --acls --xattrs \ 
      --delete-excluded \ 
      --exclude=/Downloads \ 
      /media/Windows/Users/XYZ/ \ 
      /media/Backup/btr_backup_Windows/sync/ 
btrbk -q run[/FONT]
``` 
[*]Add the following lines to /etc/btrbk/btrbk.conf
Keep daily backups for 14 days and weekly backups for 20 weeks.
```
[FONT=monospace][COLOR=#000000]volume /media/Backup/btr_backup_Windows [/COLOR]
  subvolume sync 
    snapshot_preserve_min   latest 
    snapshot_preserve       14d 20w [/FONT]
``` 
[/LIST]

**Final /etc/fstab**
```
[FONT=monospace][COLOR=#000000]UUID=[FONT=monospace]DDDDDDDD-DDDD-DDDD-DDDD-DDDDDDDDDDDD[/FONT]  /media/System_root          btrfs    defaults,subvol=/                     0       1 [/COLOR]
UUID=DDDDDDDD-DDDD-DDDD-DDDD-DDDDDDDDDDDD  /                           btrfs    defaults,subvol=@                     0       1 
UUID=[/FONT][FONT=monospace][FONT=monospace]DDDDDDDD-DDDD-DDDD-DDDD-DDDDDDDDDDDD[/FONT]  /home                       btrfs    defaults,subvol=@home                 0       2 

UUID=CCCC-CCCC                             /boot/efi                   vfat     umask=0077                            0       1 
/dev/mapper/vgkubuntu-swap_1               none                        swap     sw                                    0       0 

UUID=[FONT=monospace][FONT=monospace]XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX  [/FONT][/FONT]/media/UserData_root        btrfs    defaults,subvol=/                     0       1 
[/FONT][FONT=monospace][FONT=monospace]UUID=XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX  /media/UserData             btrfs    defaults,subvol=@                     0       1 
UUID=YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY  /media/Backup               btrfs    defaults                              0       1[/FONT] 
UUID=[FONT=monospace][COLOR=#000000]ZZZZZZZZZZZZZZZZ[/COLOR][/FONT]                      /media/Windows              ntfs     defaults,nls=utf8,umask=007,gid=46    0       0   
[/FONT]
```

**Final **[FONT=monospace][COLOR=#000000]**/etc/btrbk.daily/btrfs_backup.sh**
[/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000][FONT=monospace][COLOR=#000000]#!/bin/sh -e [/COLOR]
rsync -az --delete \ 
      --inplace --numeric-ids --acls --xattrs \ 
      --delete-excluded \ 
      --exclude=/Downloads \ 
      /media/Windows/Users/MrLee/ \ 
      /media/Backup/btr_backup_Windows/sync/ 
btrbk -q run 
kdialog --passivepopup 'BTRBK executed' 30[/FONT][/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000]
[/COLOR]
**Final **[/FONT][FONT=monospace]**[COLOR=#000000]/etc/btrbk/btrbk.conf[/COLOR]**
[/FONT]```
[FONT=monospace][FONT=monospace][COLOR=#000000]# Enable transaction log [/COLOR]
transaction_log            /var/log/btrbk.log 

# Use long timestamp format (includes hour/minute) 
timestamp_format           long 
  
snapshot_preserve_min  latest 
snapshot_preserve      no 

# Create snapshots only if the backup disk is attached 
#snapshot_create ondemand 

target_preserve_min    no 
target_preserve        200d 30m 

snapshot_dir           btrbk_snapshots 


volume /media/Backup/btr_backup_Windows 
  subvolume sync 
    snapshot_preserve_min   latest 
    snapshot_preserve       14d 20w 

volume /media/System_root 
  target send-receive /media/Backup/btr_backup_System 
    subvolume @ 
      target_preserve  30d 10m 
    subvolume @home 
      target_preserve   30d 10m 

volume /media/UserData_root 
  target send-receive /media/Backup/btr_backup_UserData 
    subvolume @ 
      target_preserve 200d 30m 
    subvolume @/VirtualBoxVMs 
      target_preserve    *m[/FONT][/FONT]
```[FONT=monospace]

[/FONT]

---

### Post by TheFu on 2022-01-24
Worth while reading on BTRFS: [https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/](https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/)
For single-disk systems, btrfs is great.  Or if each btrfs volume is limited to 1 physical storage device, that can work too.

All rsync-based versioned backups use something called hardlinks.  Those are great for speed and efficient performance, but lose the owner, group, permissions and ACLs over time, with any changes that happen.  Hardlinks are part of the file system, so it is very important that the backup storage use a native Linux file system, not a Windows (NTFS, FAT32, exFAT) one.  They won't support hardlinks and they don't support owners, groups, and Unix-style ACLs in the ways that Linux/Unix works.

---

### Post by bruzzlee-ch on 2022-01-24
> **TheFu said:**
> Worth while reading on BTRFS: [https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/](https://arstechnica.com/gadgets/2021/09/examining-btrfs-linuxs-perpetually-half-finished-filesystem/)
For single-disk systems, btrfs is great.  Or if each btrfs volume is limited to 1 physical storage device, that can work too.

All rsync-based versioned backups use something called hardlinks.  Those  are great for speed and efficient performance, but lose the owner,  group, permissions and ACLs over time, with any changes that happen.   Hardlinks are part of the file system, so it is very important that the  backup storage use a native Linux file system, not a Windows (NTFS,  FAT32, exFAT) one.  They won't support hardlinks and they don't support  owners, groups, and Unix-style ACLs in the ways that Linux/Unix  works.

Yes. You are right. It seems that btrfs-raid is not yet mature. (I've never tested that)
But for the majority of users, a single disk system is what they need and use. I have been using btrfs for a few years without any issues. 
NAS companies like Synology are using btrfs as part of their snapshot solution. [https://www.synology.com/en-global/dsm/Btrfs](https://www.synology.com/en-global/dsm/Btrfs)
The (my) problem with the rsync-based versioned backup was that even deleting a single snapshot (~800 GB) took a long time. In my case, >10 minutes per snapshot  (rsync --delete)

With the described btrfs solution, only the changes will be transferred to the backup disk. And compared to rsync, the changes are processed by the btrfs during runtime. So there is no need for a *over all scan". That's what makes it so fast in my case.

---

### Post by TheFu on 2022-01-24
Perhaps **rsync --delete** doesn't do what you think it does?  To remove an entire "back-in-time" set/version, just find the yyyy-dd-mm directory and delete it and everything below it.  This can be automated easily using a **find /path/to/backups -ctime +181 -type d -delete**  That will find all the directories created over 181 days ago and delete them.  Be certain to get the /path/to/backups correct. Wouldn't want to delete old files anywhere else on the system, right? Should remove the hardlinked files inside those directories too. I didn't test it, so please, please, test it first somewhere safe.

I just did an rsync --delete of 16TB of data - took 27 seconds. No SSDs involved, but only 1 new file was transferred (src-->target) and none were removed. I'd run the same script (best to script these things) earlier today which updated about 10G of files added over the weekend. 

Regardless, Timeshift with btrfs IS an excellent backup tool and technique.  I don't think I'd use timeshift without btrfs. I think there are better solutions, but anything people do to make versioned backups is better than not doing something.

---

### Post by bruzzlee-ch on 2022-01-25
> **TheFu said:**
> Perhaps **rsync --delete** doesn't do what you think it does?  To remove an entire "back-in-time" set/version, just find the yyyy-dd-mm directory and delete it and everything below it.  This can be automated easily using a **find /path/to/backups -ctime +181 -type d -delete**  That will find all the directories created over 181 days ago and delete them.  Be certain to get the /path/to/backups correct. Wouldn't want to delete old files anywhere else on the system, right? Should remove the hardlinked files inside those directories too. I didn't test it, so please, please, test it first somewhere safe.

I just did an rsync --delete of 16TB of data - took 27 seconds. No SSDs involved, but only 1 new file was transferred (src-->target) and none were removed. I'd run the same script (best to script these things) earlier today, which updated about 10G of files added over the weekend. 

Regardless, Timeshift with btrfs IS an excellent backup tool and technique.  I don't think I'd use timeshift without btrfs. I think there are better solutions, but anything people do to make versioned backups is better than not doing something.

I've compared:
[LIST]
[*]rsync -a --delete /path/to/empty_dir/ $dir 
[*]rm -r $dir 
[*]find $dir -delete 
[/LIST]
Everything took > 10 minutes per snapshot (I made a script to remove the old snapshots of Back-In-Time) rsync -a --delete was the fastest.
I don't know the exact reason, it could be that btrfs also had an effect on rsync.... Or the data amount which was actually: 1.3 TiB, 600000 files, 120000 subfolders.
I really can't tell, as I already removed all that data.

---

### Post by fitbeet3198 on 2023-01-20
I also met, but solved

---

