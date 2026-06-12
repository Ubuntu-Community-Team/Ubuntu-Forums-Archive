---
title: "Software raid corrupted?"
date: 2019-12-10
forum: Server Platforms
---

### Post by anytimesoon2 on 2019-12-10
After a power cut, I switched my server up again. It has an ssd as the boot drive and three spinning disk drives in a RAID5 configuration. Since the power cut, the server won't boot and goes straight to emergency mode.

Running `fdisk -l` doesn't bring up the raid partition at all.

I tried running `fsck` on my boot partition, and it's fine, so I don't know why the machine doesn't boot.

When I run `fsck` on the raid partition, I get this message:
fsck.ext4: Invalid argument while tring to open /dev/md0

The superblock could not be read or does not describe a valid ext2/ext3/ext4 filesystem. If the device is valid and it really contains an ext2/ext3/ext4 filesystem (and not swap or ufs or something else), then the superblock is corrut, and you might try running e2fsck with an alternate superblock


So I tried `fsck -a /dev/md0 -b 8193`

But that gives me the same message.



Have I lost all my data? Is the easiest thing at this point to just wipe everything and start again from backups? I don't know if I have everything from the last few days backed up, so I'd rather avoid that, if possible.

---

### Post by rsteinmetz70112 on 2019-12-10
Calm Down and take a deep breath.

I think we need a little more information on you set up.

I'm guessing the SSD has the boot and OS on it. What partitions are one it?
I'm guessing the RAID Array is a for date either application or /home.

If you are dropped into emergency mode are there any error messages before that?
What prompt do you get? Can you give the root password and get a command line?
Is the ARRAY hardware or mdadm or something else?

---

### Post by slickymaster on 2019-12-10
*Thread moved to **Server Platforms**.*

---

### Post by anytimesoon2 on 2019-12-10
Yes, the SSD has the boot and OS. The partitions are:
/dev/sdb1  512M EFI System
/dev/sdb2 23.9G Linux Filesystem
/dev/sdb3 4.9G Linux Swap

The RAID is mdadm, and was used only as data storage for media. Mostly photos, music and videos.

I'm not sure how to show the full error messages I get on boot, so I've taken a picture. It shows the full error message I get, as well as the prompt. I can get past the password and to the command prompt

[ATTACH=CONFIG]284599[/ATTACH]

Edit:
smaller version of same image:
[IMG]https://i.imgur.com/IF5buIG.jpg?1[/IMG]

---

### Post by SeijiSensei on 2019-12-10
Well the error messages say there's a physical problem with /dev/sda1. Is that part of the RAID set?  If, after using emergency mode, you run 
```
mdadm --detail /dev/md*
```
what do you see? Is /dev/sda1 marked as faulty? If not, you might be able to get things running with
```

mdadm /dev/mdX --fail /dev/sda1
mdadm /dev/mdX --remove /dev/sda1

```
Replace mdX with the appropriate name for the RAID device on your system like md0 or md127.  If the drive is already marked as faulty, you can skip the "--fail" step.

Make sure you have a replacement drive handy, since you'll lose all the data if a second drive fails in a RAID5 setup.

---

### Post by anytimesoon2 on 2019-12-10
So this is very odd...

mdadm --detail /dev/md0

gives this info:
Version: 1.2
Raid level: raid0
Total devices: 2
Persistence: Superblock is persistent

State: inactive

It then lists /dev/sdd1 and /dev/sdc1 as the two devices

This was a three drive RAID5 yesterday. I swear!

---

### Post by slickymaster on 2019-12-10
Please do not post large images into your posts. Many of our users have slow internet connections and data limits. Large images can take a long time to load -- and may even cost a user extra money. Use the attachment functionality provided by the paperclip button above the text entry box.

---

### Post by rsteinmetz70112 on 2019-12-10
Try this 

```
cat /proc/mdstat
```

post the results

Most likely there is an error somewhere causing the array not to be initiated correctly. The error may not be related to the disks or to mdadm.

---

### Post by rsteinmetz70112 on 2019-12-10
You can also try :

```
sudo mdadm /dev/md0 -A --scan
sudo mount -a
```

---

### Post by anytimesoon2 on 2019-12-10
This is the output for: cat /proc/mdstat


Personalities: [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0: inactive sdd1[3] (S) sdc1[1] (S)
         3906764959 blocks super 1.2

unused devices: <none>

---

### Post by anytimesoon2 on 2019-12-10
the output for 

mdadm /dev/md0 -A --scan

I've had to upload another image, which I've tried to keep as small as possible
[IMG]https://i.imgur.com/8BdOM3q.jpg[/IMG]

---

### Post by darkod on 2019-12-10
Is it possible to copy/paste the text output instead of images? It really helps to get the full picture.

If you can, please post the whole output in CODE tags (for easier reading) instead of trying to "explain" it like with the --detail command you were asked to run.

If you want to try saving your data, you should still be able to. Just be very careful which commands you run.

We would need the output of both array state and each member device state:
```
sudo mdadm --detail /dev/md0
sudo mdadm --examine /dev/sdc1
sudo mdadm --examine /dev/sdd1
```

That should be enough to start with. Don't do anything else right now, not even fsck, etc...

---

### Post by TheFu on 2019-12-10
First, are you booting the OS normally and having trouble accessing the RAID storage?  If not, let's fix the boot in the OS first.

sudoedit /etc/fstab
Then comment out the line with md0/md1, save the file, reboot.
It should boot find now.

To get data off the machine, store the output in files, perhaps on a flash drive, then move them to the workstation you are posting from:
Do that using something like this:
```
sudo mdadm --detail /dev/md0  2&>1 | tee -a /tmp/stuff.mdadm
sudo mdadm --examine /dev/sdc1 2&>1 | tee -a /tmp/stuff.mdadm
sudo mdadm --examine /dev/sdd1 2&>1 | tee -a /tmp/stuff.mdadm

```
The file you want to copy is /tmp/stuff.mdadm

Simple.

As for the error, it could be a failing SATA port, failing/loose cable, or some issue in the HDD.  I would ensure my backups were perfect as my first step.  RAID never replaces backups.

---

### Post by anytimesoon2 on 2019-12-10
> **darkod said:**
> Is it possible to copy/paste the text output instead of images? It really helps to get the full picture.

If you can, please post the whole output in CODE tags (for easier reading) instead of trying to "explain" it like with the --detail command you were asked to run.

If you want to try saving your data, you should still be able to. Just be very careful which commands you run.

We would need the output of both array state and each member device state:
```
sudo mdadm --detail /dev/md0
sudo mdadm --examine /dev/sdc1
sudo mdadm --examine /dev/sdd1
```

That should be enough to start with. Don't do anything else right now, not even fsck, etc...

Sorry, I couldn't figure out how to do code tags. On other platforms it's just back ticks, but that didn't seem to work here.

As with copying the code. I wish I could, as that would make it easier for everyone. I'm not sure how to even start with that, though, as I can't boot the machine. At the moment, I'm typing these comments on my laptop. Is there a way to copy the output of the commands you suggested? I'll type it all out in code tags as best I can for now


mdadm --detail /dev/md0
```

/dev/md0:
  version: 1.2
  Raid level: raid0
  Total devices: 2
  Persistence: Superblock is persistent

  State: inactive

  Name: Apollo:0 (local to host Apollo)
  UUID: bda4d60b:67008be9:82345b45:2c2b7f6c
  Events: 678612


  Number    Major    Minor    RaidDevice
       -            8          49            -            /dev/sdd1
       -            8          33            -            /dev/sdc1


```


sudo mdadm --examine /dev/sdc1
```

/dev/sdc1:
  Magic: a92b4efc
  Version 1.2
  Feature Map: 0x0
  Array UUID: bda4d60b:67008be9:82345b45:2c2b7f6c
  Name: Apollo:0 (local to host Apollo)
  Creation Time: Sun Nov 29 16:01:11 2015
  Raid Level: raid5
  Raid devices: 3

  Available dev size: 3906764976 (1862.89 GiB 2000.26 GB)
  Array Size: 3906764972 (3725.78 GiB 4000.53 GB)
  Used dev size: 3906764972 (1862.89 GiB 2000.26 GB)
  Data offset: 262144 sectors
  Super offset: 8 sectors
  Unused space: before=262064 sectors, after=304 sectors
  State: clean
  Device UUID: 3c6435e2:10604cd8:6b457ac1:1e4342b1

  Update time: Tue Dec 10 10:08:10 2019
  Checksum: a0656d80 - correct
  Events: 678612

  Layout: left-symmetric
  Chunk size: 64k

  Device role: active device 1
  Array state: AAA ('A' == active, '.' == missing, 'R' == replacing)

```



sudo mdadm --examine /dev/sdd1
```

/dev/sdd1:
  Magic: a92b4efc
  Version 1.2
  Feature Map: 0x0
  Array UUID: bda4d60b:67008be9:82345b45:2c2b7f6c
  Name: Apollo:0 (local to host Apollo)
  Creation Time: Sun Nov 29 16:01:11 2015
  Raid Level: raid5
  Raid devices: 3

  Available dev size: 3906764943 (1862.89 GiB 2000.26 GB)
  Array Size: 3906764972 (3725.78 GiB 4000.53 GB)
  Used dev size: 3906764972 (1862.89 GiB 2000.26 GB)
  Data offset: 262144 sectors
  Super offset: 8 sectors
  Unused space: before=262056 sectors, after=271 sectors
  State: clean
  Device UUID: e9c714d8:f7fc11e7:44389e68:21c89b35

  Update time: Tue Dec 10 10:08:10 2019
  Bad Block Log: 512 entries available at offset 72 sectors
  Checksum: a0656d80 - correct
  Events: 678612

  Layout: left-symmetric
  Chunk size: 64k

  Device role: active device 2
  Array state: AAA ('A' == active, '.' == missing, 'R' == replacing)

```

---

### Post by anytimesoon2 on 2019-12-10
> **TheFu said:**
> First, are you booting the OS normally and having trouble accessing the RAID storage?  If not, let's fix the boot in the OS first.

sudoedit /etc/fstab
Then comment out the line with md0/md1, save the file, reboot.
It should boot find now.

To get data off the machine, store the output in files, perhaps on a flash drive, then move them to the workstation you are posting from:
Do that using something like this:
```
sudo mdadm --detail /dev/md0  2&>1 | tee -a /tmp/stuff.mdadm
sudo mdadm --examine /dev/sdc1 2&>1 | tee -a /tmp/stuff.mdadm
sudo mdadm --examine /dev/sdd1 2&>1 | tee -a /tmp/stuff.mdadm

```
The file you want to copy is /tmp/stuff.mdadm

Simple.

As for the error, it could be a failing SATA port, failing/loose cable, or some issue in the HDD.  I would ensure my backups were perfect as my first step.  RAID never replaces backups.

Luckily, I have some pretty up to date back ups from last week, so I'm not too worried about the data. I just don't want to go through all the trouble of setting it all up again

---

### Post by TheFu on 2019-12-10
> **anytimesoon2 said:**
> Luckily, I have some pretty up to date back ups from last week, so I'm not too worried about the data. I just don't want to go through all the trouble of setting it all up again

Restoring a backup should take less than 45 minutes total and about 10 minutes of your time to get back a system that feels exactly the same as it was previously. The restore method should work to different hardware too, so not tied to any specific CPU brand or storage setup.

Did you comment out the md0 line in the fstab? Is the OS booting again?

---

### Post by anytimesoon2 on 2019-12-11
> **TheFu said:**
> Restoring a backup should take less than 45 minutes total and about 10 minutes of your time to get back a system that feels exactly the same as it was previously. The restore method should work to different hardware too, so not tied to any specific CPU brand or storage setup.

Did you comment out the md0 line in the fstab? Is the OS booting again?

I have. That worked like a charm. The system is fine. It's just the raid is a bit screwy. When I open "disks", I can see the raid-5 array volume, but it says it's 0.0kb (o bytes). All disks are showing without errors (including /dev/sda).

My backup is offsite, and there's a fair amount of it, so it would take a while to download everything. I'm still confident this is salvageable

---

### Post by TheFu on 2019-12-11
Does /proc/mdstat still show only 2 devices being used?  

Have you checked the SMART data for all 3 disks?  Adding back a disk that is about to fail or already failed won't be good.

Some output above says that all three are seen by 2 commands. Did you jiggle the cables? Are all 3 disks spinning?  
If three disks are being seen by the OS, but /proc/mdstat isn't showing them all in the array, then you can add the missing disk back with
```
$ sudo mdadm /dev/md0 -a /dev/sdf1
``` obviously, sdf1 needs to be the correct, missing, disk partition.
Then check /proc/mdstat for any rebuilding of the data. You can also look at 
```
sudo mdadm --detail /dev/md0
```
For *spare rebuilding*.  I haven't used RAID5 in a long time and only used it with 4 disks.
If the rebuilding is going too slow, there are methods to speed it up, at the expense of current disk access.

I had a disk connector in an external array that kept coming loose for about 2 yrs before I finally bought a locking SATA connector. Since swapping the connectors out (they are all 90deg connectors since), the assembled arrays have been upgraded to larger disks, RAID1, and working perfectly well over 10 yrs.

BTW, to make 'code tags', use the Adv Editor and the '#' button 
or
use the 'quote tag' button on the simple editor and replace the "QUOTE" parts with 'code' or CODE. Case doesn't matter.

---

### Post by anytimesoon2 on 2019-12-11
Here's what I get:


sudo cat /proc/mdstat
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdd1[3](S) sdc1[1](S)
      3906764959 blocks super 1.2
       
unused devices: <none>

```

sudo mdadm --detail /dev/md0
```

/dev/md0:
        Version : 1.2
     Raid Level : raid0
  Total Devices : 2
    Persistence : Superblock is persistent

          State : inactive

           Name : Apollo:0  (local to host Apollo)
           UUID : bda4d60b:67008be9:82345b45:2c2b7f6c
         Events : 678612

    Number   Major   Minor   RaidDevice

       -       8       49        -        /dev/sdd1
       -       8       33        -        /dev/sdc1

```


sudo mdadm /dev/md0
```

/dev/md0: is an md device which is not active

```

sudo mdadm /dev/md0 -a /dev/sda1
```

mdadm: Cannot get array info for /dev/md0

```

I guess I'm getting those last two because /dev/md0 was commented out of fstab

Still only seeing two devices, which is really weird.

Thank you to everyone for all of your help and support so far. I really appreciate it

---

### Post by TheFu on 2019-12-11
Commenting out of fstab doesn't impact mdadm stuff, just the mounting.

SMART data for /dev/sda?  Definitely need to check that.

These are all SATA/SAS connected, right?

---

### Post by anytimesoon2 on 2019-12-11
All disks are SATA connected to the motherboard. I've checked all physical connections and everything seems fine

SMART data test fails within a minute on sda1. It gets to 90% remaining saying "disk is OK, one bad sector", then fails before finishing

---

### Post by TheFu on 2019-12-11
Did you try using a different controller port and cable?

Time for a new disk.

This disk might be suitable for sneaker-net needs, but probably not for backups.

---

### Post by anytimesoon2 on 2019-12-11
I've tried swapping the cables around, but it's still giving me the same grief. I guess that disk is ready for destruction. Kind of annoying that it's the youngest disk in the array by a couple years.

All the other disks pass the SMART test. So what I don't understand now is I thought a raid5 would continue working if a disk fails like this.

How can I safely remove the drive and replace it? I found this tutorial, but I don't want to do anything that might compromise the other two disks: [https://www.tjansson.dk/2013/12/replacing-a-failed-disk-in-a-mdadm-raid/](https://www.tjansson.dk/2013/12/replacing-a-failed-disk-in-a-mdadm-raid/)

I'm also not sure if it'll work, considering /dev/md0 thinks it's a raid0

---

### Post by TheFu on 2019-12-11
The individual partitions know they are RAID5.

Do like SeijiSensei said in post #5 to have the bad disk removed.
After you pull the bad disk and put in a new one, partition it exactly the same (I'd use **sfdisk** for that), then do the **mdadm /dev/md0 -a /dev/sdXY** to reassemble it.

You can watch the progress in /proc/mdstat as it rebuilds.

---

### Post by darkod on 2019-12-11
Wow guys, you really got it going... :)

No suggestions to simply reassemble the array though. And that is the best way forward.

The --examine shows sdc1 and sdd1 know they belong to the same raid5 array. They even have identical Events counter which is very good when rescuing mdadm. Ignore the fact md0 assembles as raid0 right now, that is not important.

First stop the current "bad" md0 and then simple tell sdc1 and sdd1 to assemble the array (it should work with 2 members out of 3).
```
sudo mdadm --stop /dev/md0
sudo mdadm --assemble --verbose --force /dev/md0 /dev/sdc1 /dev/sdd1
```

See what output that gives you.

PS. I just noticed reassemble was mentioned in the previous post. I wouldn't worry about sda1 at the moment. First thing is to get the array running. After that, whether you decide to try adding sda1 as it is, or replacing sda with new disk, we'll see...

---

### Post by anytimesoon2 on 2019-12-11
Doing that returns an error:

sudo mdadm /dev/md0 --fail /dev/sdc1
```

mdadm: Cannot get array info for /dev/md0

```

---

### Post by anytimesoon2 on 2019-12-11
> **darkod said:**
> Wow guys, you really got it going... :)

No suggestions to simply reassemble the array though. And that is the best way forward.

The --examine shows sdc1 and sdd1 know they belong to the same raid5 array. They even have identical Events counter which is very good when rescuing mdadm. Ignore the fact md0 assembles as raid0 right now, that is not important.

First stop the current "bad" md0 and then simple tell sdc1 and sdd1 to assemble the array (it should work with 2 members out of 3).
```
sudo mdadm --stop /dev/md0
sudo mdadm --assemble --verbose --force /dev/md0 /dev/sdc1 /dev/sdd1
```

See what output that gives you.

PS. I just noticed reassemble was mentioned in the previous post. I wouldn't worry about sda1 at the moment. First thing is to get the array running. After that, whether you decide to try adding sda1 as it is, or replacing sda with new disk, we'll see...


Just a quick note, since the suggestions to try swapping cables, the faulty drive is now /dev/sdc. With that in mind, I've tried the above, with some success:

sudo mdadm --assemble --verbose --force /dev/md0 /dev/sdb1 /dev/sdd1

```

mdadm: looking for devices for /dev/md0
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 2.
mdadm: no uptodate device for slot 0 of /dev/md0
mdadm: added /dev/sdd1 to /dev/md0 as 2
mdadm: added /dev/sdb1 to /dev/md0 as 1
mdadm: /dev/md0 has been started with 2 drives (out of 3).

```


Only thing now, is that I don't know how to access the data on it...

---

### Post by darkod on 2019-12-11
One small step at a time, especially in a rescue operation... So, the array assembled.

To quickly check data, you can temporarily mount it as read-only on any empty mount point. I repeat this would be temporarily to check content only.

After that you will need to see if you are buying a new disk or what... Meanwhile you can decide to keep using the array.

```
sudo mkdir /mnt/rescue
sudo mount -o ro /dev/md0 /mnt/rescue
ls /mnt/rescue
```

The data should be there. I said mounting read-only to avoid writing anything to the array while you are still checking it out and confirming data integrity. Dismount it after that:
```
sudo umount /mnt/rescue
```

---

### Post by anytimesoon2 on 2019-12-11
I was unable to mount. I got this error:

sudo mount -o ro /dev/md0 /mnt/rescue

```

mount: /dev/md0: more filesystems detected. This should not happen,
       use -t <type> to explicitly specify the filesystem type or
       use wipefs(8) to clean up the device.

```

---

### Post by darkod on 2019-12-11
That doesn't sound good. What does blkid say for filesystem detected on the assembled array?
```
sudo blkid
```

---

### Post by anytimesoon2 on 2019-12-11
sudo blkid

```

/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="C135-B169" TYPE="vfat" PARTUUID="d7acf241-6f22-4c26-956f-68587f2088cd"
/dev/sda2: UUID="8b94f73d-98dc-4567-98dc-1bb8c1799e4b" TYPE="ext4" PARTUUID="b5cc595f-7d36-4a55-931d-ce8e5b32b02d"
/dev/sda3: UUID="eee730b6-79ad-4fe3-8f6f-76e2eac2c62b" TYPE="swap" PARTUUID="11282957-6b33-4485-b37b-037aea0ea0f7"
/dev/sdb1: UUID="bda4d60b-6700-8be9-8234-5b452c2b7f6c" UUID_SUB="3c6435e2-1060-4cd8-6b45-7ac11e4342b1" LABEL="Apollo:0" TYPE="linux_raid_member"
/dev/sdd1: UUID="bda4d60b-6700-8be9-8234-5b452c2b7f6c" UUID_SUB="e9c714d8-f7fc-11e7-4438-9e6821c89b35" LABEL="Apollo:0" TYPE="linux_raid_member" PARTUUID="805de80c-7c1e-4e92-b725-eb30babceb87"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"
/dev/loop12: TYPE="squashfs"

```

---

### Post by darkod on 2019-12-11
There is no /dev/md0 in the list. Was it assembled when running the command?

---

### Post by anytimesoon2 on 2019-12-11
It said it was. It hasn't shown using fdisk since the power outage yesterday.

I can see it in the "disks" ubuntu utility, however

---

### Post by TheFu on 2019-12-11
I've never trusted **gnome-disks** .

FYI, whenver any loop devices are shown in any output from any command, it is safe to remove those unless the issue is specifically about loop devices or mounting loop devices.  Having those just crufts up the important data.  Since snap packages were introduced/forced, there are way too many loop devices showing up.

---

### Post by darkod on 2019-12-11
It almost looks like you have another partition on sdd1 somehow. Notice the output of blkid is different between sdb1 and sdd1. It should be similar, only difference should be the UUID_SUB string. But sdd1 also has some PARTUUID.

And md0 should show now in parted, fdisk, lsblk, and similar tools.

You could try mounting and specifying that the filesystem is ext4 (if that is what it was) and see how it likes it. Similar command like before (once you have the array assembled):
```
sudo mount -o ro -t ext4 /dev/md0 /mnt/rescue
```

---

### Post by rsteinmetz70112 on 2019-12-11
Earlier in the thread the OP was advised to comment out the /dev/md0 line in /etc/fstab, if it's still commented out mount may not know the fstype try```
 lsblk
``` which should show all of the drives, their partitions and the arrays they are in.

It also seems there is a drive missing possibly /dev/sdc?

---

### Post by anytimesoon2 on 2019-12-13
Thank you for your suggestions, everyone. I'm away now with work, and don't have access to the faulty machine, but I will try this when I get back next week.

---

### Post by anytimesoon2 on 2019-12-16
```

sudo mount -o ro -t ext4 /dev/md0 /mnt/rescue


mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

```


```

lsblk

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sdd      8:48   0   1.8T  0 disk 
&#9492;&#9472;sdd1   8:49   0   1.8T  0 part 
sdb      8:16   0   1.8T  0 disk 
&#9492;&#9472;sdb1   8:17   0   1.8T  0 part 
sdc      8:32   0   1.8T  0 disk 
&#9492;&#9472;sdc1   8:33   0   1.8T  0 part 
sda      8:0    0  29.3G  0 disk 
&#9500;&#9472;sda2   8:2    0  23.9G  0 part /
&#9500;&#9472;sda3   8:3    0   4.9G  0 part [SWAP]
&#9492;&#9472;sda1   8:1    0   512M  0 part /boot/efi

```

md0 won't mount, and doesn't show anywhere. This isn't looking good.

---

### Post by TheFu on 2019-12-16
IME, sometimes the only fix for a bad RAID is to wipe everything, rebuild it from scratch, and restore from backups.  I would have done that after 1.5 days of attempting to correct the array and failing. I have excellent backups.  That's the limit of my stubbornness.  We each have a different stubbornness factor.

In prior posts, a number of questions were asked, but never answered, BTW.

---

### Post by anytimesoon2 on 2019-12-16
I think you're probably right. I'll give up and start again. Thanks for all your help and time. 

I didn't notice any unanswered questions, though. I thought I answered everything that was asked.

---

### Post by darkod on 2019-12-16
But correct me if I'm wrong, you managed to manually assemble the array using one of my earlier commands, right? So even if it does not auto-assemble on boot, do it manually and check the filesystem/files.

If that works, making the array auto-assemble is piece of cake. We'll do it when we get there. I don't want to rush with giving commands until we reach each stage...

If you want to wipe and start all over, no problem of course... Your choice.

---

