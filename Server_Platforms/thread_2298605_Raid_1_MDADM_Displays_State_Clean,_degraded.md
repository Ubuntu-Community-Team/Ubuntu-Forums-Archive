---
title: "Raid 1 MDADM Displays State: Clean, degraded"
date: 2015-10-12
forum: Server Platforms
---

### Post by lingpanda on 2015-10-12
Hello,


    Hope someone can help. Several topics about raid. However many seem to be unique. Noticed the following in my syslog.

DegradedArray event detected on md device /dev/md/1



Looking at the disks I see


```
root@pfmember1:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Jan  2 09:45:43 2015
     Raid Level : raid1
     Array Size : 39035776 (37.23 GiB 39.97 GB)
  Used Dev Size : 39035776 (37.23 GiB 39.97 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Mon Oct 12 13:53:35 2015
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : pfmember1:0  (local to host pfmember1)
           UUID : fd83bcc9:898525f6:8bf4b094:db3afc1f
         Events : 20

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
root@pfmember1:~# mdadm --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Fri Jan  2 09:45:50 2015
     Raid Level : raid1
     Array Size : 1914313536 (1825.63 GiB 1960.26 GB)
  Used Dev Size : 1914313536 (1825.63 GiB 1960.26 GB)
   Raid Devices : 2
  Total Devices : 1
    Persistence : Superblock is persistent

    Update Time : Mon Oct 12 14:07:03 2015
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           Name : pfmember1:1  (local to host pfmember1)
           UUID : 177e57ce:aa907143:31c06531:b92e9b08
         Events : 99637

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       18        1      active sync   /dev/sdb2
```

How do I proceed to fix? Thanks.

---

### Post by darkod on 2015-10-12
I assume the other member of md1 was /dev/sda2. If that is the case, and since the partition was already a member of the array, the first thing to try is --re-add.
```
sudo mdadm /dev/md1 --re-add /dev/sda2
```

See how that goes.

---

### Post by lingpanda on 2015-10-12
> **darkod said:**
> I assume the other member of md1 was /dev/sda2. If that is the case, and since the partition was already a member of the array, the first thing to try is --re-add.
```
sudo mdadm /dev/md1 --re-add /dev/sda2
```

See how that goes.

Darkod,


  Didn't work.

```
mdadm: --re-add for /dev/sda2 to /dev/md1 is not possible
```

Would I be safe to run

```
mdadm --remove /dev/md1 /dev/sda2
```

and

```
mdadm -- add /dev/md1 /dev/sda2
```

to see if it will resync? Thanks.

---

### Post by darkod on 2015-10-12
It is already in removed state, as the --detail showed. So no need to run the --remove. Try the --add and if that doesn't work, try zeroing the superblock and then --add.
```
sudo mdadm /dev/md1 --add /dev/sda2
```

Or,
```
sudo mdadm --zero-superblock /dev/sda2
sudo mdadm /dev/md1 --add /dev/sda2
```

The array you are working with (in this case /dev/md1) goes before the --add option.

---

### Post by lingpanda on 2015-10-12
> **darkod said:**
> It is already in removed state, as the --detail showed. So no need to run the --remove. Try the --add and if that doesn't work, try zeroing the superblock and then --add.
```
sudo mdadm /dev/md1 --add /dev/sda2
```

Or,
```
sudo mdadm --zero-superblock /dev/sda2
sudo mdadm /dev/md1 --add /dev/sda2
```

The array you are working with (in this case /dev/md1) goes before the --add option.

I think the --add did the trick.

```
@pfmember1:~# mdadm --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Fri Jan  2 09:45:50 2015
     Raid Level : raid1
     Array Size : 1914313536 (1825.63 GiB 1960.26 GB)
  Used Dev Size : 1914313536 (1825.63 GiB 1960.26 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Mon Oct 12 15:29:38 2015
          State : active, degraded, recovering
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

 Rebuild Status : 0% complete

           Name : pfmember1:1  (local to host pfmember1)
           UUID : 177e57ce:aa907143:31c06531:b92e9b08
         Events : 101052

    Number   Major   Minor   RaidDevice State
       2       8        2        0      spare rebuilding   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2
```

I will monitor. Thanks.

---

### Post by darkod on 2015-10-12
Yes, looks like it's syncing.

---

### Post by lingpanda on 2015-10-13
> **darkod said:**
> Yes, looks like it's syncing.

Hello Darkod,


  It appears I may have a faulty disk.

```
@pfmember1:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Fri Jan  2 09:45:43 2015
     Raid Level : raid1
     Array Size : 39035776 (37.23 GiB 39.97 GB)
  Used Dev Size : 39035776 (37.23 GiB 39.97 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Mon Oct 12 13:53:35 2015
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : pfmember1:0  (local to host pfmember1)
           UUID : fd83bcc9:898525f6:8bf4b094:db3afc1f
         Events : 21

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
root@pfmember1:~# mdadm --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Fri Jan  2 09:45:50 2015
     Raid Level : raid1
     Array Size : 1914313536 (1825.63 GiB 1960.26 GB)
  Used Dev Size : 1914313536 (1825.63 GiB 1960.26 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Tue Oct 13 08:55:22 2015
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 1
  Spare Devices : 0

           Name : pfmember1:1  (local to host pfmember1)
           UUID : 177e57ce:aa907143:31c06531:b92e9b08
         Events : 109667

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       18        1      active sync   /dev/sdb2

       2       8        2        -      faulty spare   /dev/sda2
root@pfmember1:~#
```

At this point a replacement is my next course of action?

---

### Post by darkod on 2015-10-13
Probably. Especially since you don't want to risk your data. I think best to replace the disk.
If you want to, you can run smart tests with smartmontools before you decide to replace. There are plenty tutorials online how to use smartmontools.

---

### Post by lingpanda on 2015-10-13
> **darkod said:**
> Probably. Especially since you don't want to risk your data. I think best to replace the disk.
If you want to, you can run smart tests with smartmontools before you decide to replace. There are plenty tutorials online how to use smartmontools.

Do the following steps look correct to replace the faulty drive?

1.Mark as failed: ```
mdadm --manage /dev/md0 --fail /dev/sda1
```

[LIST=1] 
[/LIST]

    2. Remove: ```
mdadm --manage /dev/md0 --remove /dev/sda1
```
    
    3. Mark as failed (Not needed since already showing failed?): ```
mdadm --manage /dev/md1 --fail /dev/sda2
```

    4. Remove: ```
mdadm --manage /dev/md1 --remove /dev/sda2
```

    5. Shutdown Server, replace faulty drive

    6. Create Partitions ```
sfdisk -d /dev/sda | sfdisk /dev/sdb
```

    7. List and verify partitions ```
fdisk -l
```

    8.Add back: ```
mdadm --manage /dev/md0 --add /dev/sda1
```

    9.Add back: ```
mdadm --manage /dev/md1 --add /dev/sda2
```

    10. Watch for re-sync: ```
watch -n1 cat /proc/mdstat
```


I'm unsure of creating the partitions. Does that command look correct? Thanks.

---

### Post by darkod on 2015-10-13
Yes, the steps are correct and I am also unsure of the sfdisk step because I don't use it. I prefer to create partitions manually with parted instead of copying the layout from another disk. If you make a mistake in the sfdisk in only one letter, things can go real bad.

For example the command you wrote, I think it should be the other way around. In many tutorials sda is the current disk and sdb is the new, so you use -d to copy the layout from sda to sdb. But in your case, sdb is the good disk and replacing the faulty one should keep sda as the name of the new disk. So you would need to copy the layout from sdb to sda (all of this under the assumption the disks are called the same as now).

But depending how you plug the cables, letters can change etc... That's why I prefer little "manual labour" and do partitions manually instead of copying layout.

You can do it however you prefer of course, just make sure you do it right!!!

Except for that, the other steps are OK. Also you can note that you can skip the --manage option in the first commands (but you need to do the steps, not skip the steps). With mdadm if you use 'sudo mdadm /dev/mdX .....' it is understood as 'sudo mdadm --manage /dev/mdX ....'

That's why in my posts earlier I didn't use --manage. But that is only for manage. Other commands like --create, --assemble can't be skipped. Also options like --add, etc. You can't let mdadm guessing what you want to do... :)

---

### Post by lingpanda on 2015-10-13
Was not aware of the sudo and --manage effect. Good to know. Thanks. 

I've not created partitions from command line before. All my experience has been during install of the OS. This is my main concern. I know any little mistake could bring the other HD down. I'll read the man page on parted and see if I can figure out the commands on my own. I'll post what I think they should be. Thanks again.

---

### Post by darkod on 2015-10-13
Lets assume the new disk when replaced will still be sda, and the current good one will remain sdb.

All you need to do is:
```
sudo parted /dev/sdb   #open the parted prompt for sdb
unit MiB                             #change display units to MiB
print                                  #print the table, write down partition start end, for example lets call them p1s p1e, p2s p2e
select /dev/sda                   #change the working disk
print                                  #make sure you are working with the correct disk
mklabel msdos                    #make new msdos table
mkpart primary p1s p1e       #create new primary partition from p1s to p1e
mkpart primary p2s p2e       #create another primary partition from p2s to p2e
print                                  #confirm the table looks ok
quit                                   #quit parted
```

That's it in general. It gives great flexibility, it can work with sectors, MiB, etc. In the above I assumed the disks have msdos table, not gpt.

If you want do the first part to print sdb layout and post it, we can have a look at it. It might sound complicated reading this but once you see the table printed you will see how simple it is. Very straightforward.

---

### Post by lingpanda on 2015-10-14
```
@pfmember1:~# parted -l
Warning: Error fsyncing/closing /dev/sda: Input/output error
Retry/Ignore? i
Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Number  Start   End     Size    Type     File system  Flags
 1      1049kB  40.0GB  40.0GB  primary               raid
 2      40.0GB  2000GB  1960GB  primary               boot, raid

Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Number  Start   End     Size    Type     File system  Flags
 1      1049kB  40.0GB  40.0GB  primary               raid
 2      40.0GB  2000GB  1960GB  primary               boot, raid

Model: Linux Software RAID Array (md)
Disk /dev/md0: 40.0GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Number  Start  End     Size    File system     Flags
 1      0.00B  40.0GB  40.0GB  linux-swap(v1)

Model: Linux Software RAID Array (md)
Disk /dev/md1: 1960GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop
Number  Start  End     Size    File system  Flags
 1      0.00B  1960GB  1960GB  ext4
```

Not sure why I receive ```
Warning: Error fsyncing/closing /dev/sda: Input/output error
 Retry/Ignore? I
```

I like how this gives me the serial number of the drive. Makes Identifying so much easier. 

This I don't follow. ```
mkpart primary p1s p1e      
``` I don't see the switches p1s or p1e in any documentation. What about creating the swap? Is all this rolled into those switches? Thanks.

---

### Post by darkod on 2015-10-14
Sorry, I confused you with p1s and p1e. I wanted to say in short Partition 1 Start, Partition 1 End. You can see the Start/End in the parted listing. You can make partitions with identical start/end points on the new disk and that's how the partitions will be identical.

For your question about swap. I use parted only to create partitions. The filesystems like ext4 or swap are done with another command outside parted. But in your case the filesystem is on top of mdX so you only need to create partitions and add them to the corresponding array. I can see md0 is swap and md1 is root.

In parted I recommended to use 'unit MiB' to show all output in MiB. As you can see now for the first partition it displays start at 1049KB and end at 40GB. Try something like:
```
parted /dev/sdb unit MiB print
```

That will print data only for sdb, your good disk. I can give you precise commands after that.

That error for sda is probably because the disk is faulty, ignore it for now.

And note that what parted displays at start is the model of the disk, not the SN. Look how both sda and sdb are the same. Because the model is Seagate ST2000DM001.

---

### Post by lingpanda on 2015-10-14
> **darkod said:**
> Sorry, I confused you with p1s and p1e. I wanted to say in short Partition 1 Start, Partition 1 End. You can see the Start/End in the parted listing. You can make partitions with identical start/end points on the new disk and that's how the partitions will be identical.

For your question about swap. I use parted only to create partitions. The filesystems like ext4 or swap are done with another command outside parted. But in your case the filesystem is on top of mdX so you only need to create partitions and add them to the corresponding array. I can see md0 is swap and md1 is root.

In parted I recommended to use 'unit MiB' to show all output in MiB. As you can see now for the first partition it displays start at 1049KB and end at 40GB. Try something like:
```
parted /dev/sdb unit MiB print
```

That will print data only for sdb, your good disk. I can give you precise commands after that.

That error for sda is probably because the disk is faulty, ignore it for now.

And note that what parted displays at start is the model of the disk, not the SN. Look how both sda and sdb are the same. Because the model is Seagate ST2000DM001.

```
@pfmember1:~# parted /dev/sdb unit MiB print
Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sdb: 1907729MiB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start     End         Size        Type     File system  Flags
 1      1.00MiB   38154MiB    38153MiB    primary               raid
 2      38154MiB  1907729MiB  1869575MiB  primary               boot, raid

```

It does display the model not serial. Doh! I'll have to be a bit careful. Thanks.

---

### Post by darkod on 2015-10-14
OK... So once you get sda replaced on the new sda you will need to do:
```
parted /dev/sda
unit MiB
mklabel msdos   #new msdos table
mkpart primary 1 38154
mkpart primary 38154 1907729
set 1 raid on   #set raid flag on 1
set 2 raid on
set 2 boot on
quit
```

That's it. That will create both partitions with correct start/end so that the size is identical to sdb. It will also activate the raid flag on both partitions and boot flag on 2. In linux the boot flag is not used but sometimes it's good to have it because some motherboards don't boot if there is no disk with the boot flag. Otherwise the boot flag is a mainly windows thing.

And as already mentioned, make SURE you are working with the correct disk. Especially before you start with mklabel.

---

### Post by lingpanda on 2015-10-16
In my haste, I forgot to issue the commands to remove the faulty HD prior to install of new HD. Now I get the dreaded 

```
error no such disk 
grub rescue
```

If this was a single HD, I wouldn't be worried. The fact it's a raid setup is. I do not know how to approach this. I actually surprised the server will not boot with the one HD still working. A ls at the prompt shows me the md0 device. Any advice? Thanks.

---

### Post by darkod on 2015-10-16
This looks like grub message, not related to mdadm. But grub should have been installed on both disks, so when you removed one it should boot from the other too. And if it is showing grub rescue that means that it does find some grub bootloader (not sure if it's the correct one though).

Speaking from mdadm point of view, this is no problem. You can even add the new disk to the array from live mode using the desktop cd. So you have two options:
1. Adding the new disk from live mode, and then repair the boot (it might work on it's own after the disk is added).

2. Repairing the boot first, but that also includes live mode.

What do you feel like?

---

### Post by lingpanda on 2015-10-16
> **darkod said:**
> This looks like grub message, not related to mdadm. But grub should have been installed on both disks, so when you removed one it should boot from the other too. And if it is showing grub rescue that means that it does find some grub bootloader (not sure if it's the correct one though).

Speaking from mdadm point of view, this is no problem. You can even add the new disk to the array from live mode using the desktop cd. So you have two options:
1. Adding the new disk from live mode, and then repair the boot (it might work on it's own after the disk is added).

2. Repairing the boot first, but that also includes live mode.

What do you feel like?

I'll go with option 1. Thanks.

---

### Post by darkod on 2015-10-16
Then do this:
1. I assume you physically installed the new disk.
2. Boot the machine with desktop cd in live mode.
3. Add mdadm package (not included by default in live mode) and assemble known arrays:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan (this should assemble both arrays with one member present and one missing)
```
4. Check whether old disk is sdb and new sda or the other way around.
5. In terminal open parted for the correct (new) disk and create the partitions like we discussed previously.
6. Do the --add commands to add the partitions to md0 and md1. It doesn't matter that you are in live mode.
7. Wait for the sync to finish, checking it out periodically.

After the rebuild finishes, you can check if the machine will boot by itself. If that grub error still shows, we will work from live mode to fix it.

---

### Post by lingpanda on 2015-10-16
I receive a error when issuing 

```
mklabel msdos
```

Input/Output Error on read /dev/sda. Ignore retry cancel. Do I need to format the drive prior to creating the label? Thanks.

---

### Post by darkod on 2015-10-16
Is that the new disk? The old disk was giving errors, if the new one does the same maybe it's connection problems, not the disk?

No, you don't need to format it before creating new partition table. You format partitions, and to create partitions you need to have a new blank table created first.

---

### Post by lingpanda on 2015-10-16
It's the new drive. I'll look to see if maybe it's a sata cable that is bad. However I do not see the faulty drive in the bios. I do see the new drive. I guess in the meantime I would like to try and bring the good drive back up. How do I get the one drive to at least boot without disturbing it's current raid configuration? Thanks.

---

### Post by darkod on 2015-10-16
Is the good drive still /dev/sdb? I am asking because with adding and removing drives that can change. In live mode install the mdadm package and do the assemble scan as per the previous post. That should bring up the arrays.

Double check which array is what (is md0 still swap and md1 the root). Lets say md1 is still root and the good disk is still sdb.

A simple way to try installing correct grub on the MBR is:
```
sudo mount /dev/md1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdb
```

That allows you in live mode to temporarily mount md1 at /mnt, and then use that as parameter to tell grub-install where is the root partition mounted. The last parameter in grub-install is where you want to install grub, in this case /dev/sdb.

This is the simplest. Lets see if it works or a more complex procedure will be needed.

Also, one note... If you left the faulty disk connected it might still be sda and the new disk might be sdc. That might explain the error parted gives you. Always check that you are working with correct disk, and all disks that you have. A quick way for that is also parted:
```
sudo parted -l
```

---

### Post by lingpanda on 2015-10-19
This is what parted displays within live. Both good and faulty drive installed.

```
 sudo parted -l
Model: ATA ST2000DM001-1CH1 (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  40.0GB  40.0GB  primary               raid
 2      40.0GB  2000GB  1960GB  primary               boot, raid


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

Model: Linux Software RAID Array (md)
Disk /dev/md0: 40.0GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  40.0GB  40.0GB  linux-swap(v1)


Model: Linux Software RAID Array (md)
Disk /dev/md1: 1960GB
Sector size (logical/physical): 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  1960GB  1960GB  ext4
```

It appears sda is now the good drive? Is it possible for sda and sdb to swap like that? I can't imagine the faulty drive is now good and vice versa. Should I attempt to install grub on sda? Thanks.

Just reread your prior post. I wonder if this was my issue.

"Also, one note... If you left the faulty disk connected it might still  be sda and the new disk might be sdc. That might explain the error  parted gives you. Always check that you are working with correct disk,  and all disks that you have. A quick way for that is also parted:"

---

### Post by darkod on 2015-10-19
Yes, you can try to install grub to /dev/sda.

But I am confused about one thing. You say "both good and faulty drive installed". I thought you bought a new disk and replaced the faulty, no? Are you still running with the disks that you had, or you installed a new one?

If the faulty disk failed further and is not recognized by BIOS now, then the good disk that was earlier sdb will now be sda because it is considered the only disk in the system. Under the assumption the failed is not even recognized. In such case the drive letter will "move" because when you have only one disk detected by the system it will always be sda.

---

### Post by lingpanda on 2015-10-19
> **darkod said:**
> Yes, you can try to install grub to /dev/sda.

But I am confused about one thing. You say "both good and faulty drive installed". I thought you bought a new disk and replaced the faulty, no? Are you still running with the disks that you had, or you installed a new one?

If the faulty disk failed further and is not recognized by BIOS now, then the good disk that was earlier sdb will now be sda because it is considered the only disk in the system. Under the assumption the failed is not even recognized. In such case the drive letter will "move" because when you have only one disk detected by the system it will always be sda.

Yes. You are correct. 

I went ahead and removed the faulty drive. I did not attempt to reinstall the replacement drive. It's now running with just one drive. 

This is what I get now.

```
sudo mount /dev/md1/mnt
mount: can't find /dev/md1/mnt in /etc/fstab or /etc/mtab
```

I think I altered this fstab if memory serves me. If so it would of been similar to this.

```
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/pfdc1-root /               ext4    errors=remount-ro,user_xattr,acl,barrier=1 1       1
# /boot was on /dev/sda1 during installation

UUID=54f12064-e95b-4f55-b500-d950981f7f5d /boot           ext2    defaults        0       2
/dev/mapper/pfdc1-swap_1 none            swap    sw              0       0
```

Ok this is my fault. I didn't enter a space between the sudo mount /dev/md1 **/mnt**

---

### Post by lingpanda on 2015-10-19
I was able to mount the drive and backup any contents I need, just in case.  I'm unable to install grub. Grub is missing from usr/sbin. I used locate and found the only instance of grub on /mnt/usr/sbin. I get command not found if issuing.

```
sudo grub-install
```

I tried the unc path to grub

```
/mnt/usr/sbin/sudo grub-install --root-directory=/mnt /dev/sda
```

it fails when running grub-setup. Command not found. I tried adding /mnt/usr/sbin to $PATH. Still fails. Any idea? Thanks.

---

### Post by lingpanda on 2015-10-19
I finally have the system up and running again. :D

When I couldn't find grub it got me thinking. Maybe I need to use chroot. This link [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd) along with your initial post fixed it. I'll tackle fixing raid shortly.

---

### Post by darkod on 2015-10-19
Glad you got it sorted. As I said, that short procedure is the quick way to start with. If that doesn't work the chroot procedure is the longer one to try. I am surprised grub-install would not be available in live mode. I haven't seen such a case so far. There is no need to add any paths or anything, you should be able to issue sudo grub-install from where ever.

Anywa, onto the raid now...

---

### Post by lingpanda on 2015-10-21
Small update. It looks as if I may actually have issues with the server box itself. Now I not seeing the good HD in the bios as well. The 'faulty' HD might just end up being good.

---

