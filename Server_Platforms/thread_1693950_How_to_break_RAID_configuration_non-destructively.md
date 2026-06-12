---
title: "How to break RAID configuration non-destructively"
date: 2011-02-23
forum: Server Platforms
---

### Post by itismike on 2011-02-23
I'm looking for help breaking a software RAID 1 disk array so I can remove one of the drives permanently. I've found a couple suggestions to make the drive 'forget' that it is a RAID drive by "zeroing out their md superblocks", but I don't know enough about superblocks to know if this is destructive or not. 

I used [this guide]("https://help.ubuntu.com/community/Installation/SoftwareRAID") to create my RAID-1 and it is working fine. This is my current setup:
```
$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdb1[1] sda1[0]
      149864384 blocks [2/2] [UU]

md1 : active raid1 sdb5[1] sda5[0]
      6382528 blocks [2/2] [UU]

unused devices: <none>

``` 
Following the [steps to remove the RAID]("https://help.ubuntu.com/community/Installation/SoftwareRAID#Disk%20Array%20Operation"), I immediately get errors:```
$ sudo mdadm --stop /dev/md0
mdadm: fail to stop array /dev/md0: Device or resource busy
```

Do I need to boot from a live CD and perform the same commands on an unmounted filesystem?

---

### Post by YesWeCan on 2011-02-23
Hi. You won't be able to stop the array if any of its files are being used. That includes having a terminal open and cd'ed to a directory on the array. Are you running your OS off the array?


I guess you are asking how to convert a RAID 1 into two single, raidless drives. Otherwise the drive that remains would have to run as a degraded array all the time. IOW can a RAID 1 member with a zero'ed superblock be mounted without using mdadm?

I don't know but I would like to know. I don't know if/how mdadm does chunks on RAID 1.

---

### Post by itismike on 2011-02-23
yes, that is exactly what I want to do: take my current RAID-1 disks and turn them into independent disks. One will remain in the system unchanged (hopefully!), and I'll be adding a larger data disk to accompany it, foregoing RAID in the new setup.

---

### Post by YesWeCan on 2011-02-23
While we wait for the gurus to arrive, would you mind posting the output of 'sudo fdisk -l' and put code tags around it (use the # button).

---

### Post by itismike on 2011-02-23
Good idea. Thanks Yes!
```
$ sudo fdisk -l

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d19ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18658   149864448   fd  Linux raid autodetect
/dev/sdb2           18658       19453     6382593    5  Extended
/dev/sdb5           18658       19453     6382592   fd  Linux raid autodetect

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003e8d8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18658   149864448   fd  Linux raid autodetect
/dev/sda2           18658       19453     6382593    5  Extended
/dev/sda5           18658       19453     6382592   fd  Linux raid autodetect

Disk /dev/md1: 6535 MB, 6535708672 bytes
2 heads, 4 sectors/track, 1595632 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table

Disk /dev/md0: 153.5 GB, 153461129216 bytes
2 heads, 4 sectors/track, 37466096 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

---

### Post by rubylaser on 2011-02-23
You're on the right track, but I'm assuming that this is your OS drive.  If so, you'll need to boot from a livecd, then apt-get install mdadm.  Then you can zero the superblocks like this...
```
sudo mdadm --zero-superblock /dev/sda1
sudo mdadm --zero-superblock /dev/sdb1
sudo mdadm --zero-superblock /dev/sda5
sudo mdadm --zero-superblock /dev/sdb5
```
You'll need to remove /etc/mdadm/mdadm.conf from the remaining drive, and update /etc/fstab to mount the remaining drive by UUID, and finally update grub to reflect booting from the individual disk partition rather than the RAID array.

Before you potentially break your install, you might want to work out all of these steps in a virtual machine first.

---

### Post by itismike on 2011-02-23
Wow. Thanks for explaining it Ruby. I had no idea it would be so involved. I'll save this project for a rainy day.

---

### Post by YesWeCan on 2011-02-23
Thanks Guru! ;)
You can see in the fdisk output that your partitions are labelled as type "Linux RAID autodetect" ID=fd. These can be changed to "linux" ID=83 using the Disk Utility under the System/Administration menu of the live CD.

---

### Post by SeijiSensei on 2011-02-24
I've found I could mount one of my RAID1 disks as a normal filesystem.  If the RAID uses /dev/sda1 and /dev/sda2, I've found I could simply mount /dev/sda1 and use the filesystem as ext3/4.  This can be invaluable when one of the drives dies.  I don't think I needed to change the partition identifier from fd to 83 either.

---

### Post by rubylaser on 2011-02-24
Yes, this is true, and you don't need to change the partition type.  The OP asked about how to completely remove the RAID1 array, so I posted some ideas.  The easiest method would be to remove the md module or remove mdadm if you aren't going to use it anyways.

---

### Post by YesWeCan on 2011-02-24
Any idea what the partition ID is for?
I assumed it would be noticed by the md drivers or something during boot. Suppose you have a raid and the ID is not set to autodetect, does that mean the raid would not be assembled during the boot? Or is the ID just some defunct thing?

---

### Post by rubylaser on 2011-02-25
That's what I always assumed, but I was posting in a thread for luks encrypted mdadm (something I've never bothered with), and the OP couldn't get the array to assemble correctly with the partition id's set as linux raid autodetect.  [http://ubuntuforums.org/showthread.php?t=1691972]("http://ubuntuforums.org/showthread.php?t=1691972") He had to set them to 83 (linux).  I think it's still a good idea to set it properly, but I don't think it's as important as I've always believed.

---

### Post by ScottEChapman on 2011-03-28
This is exactly what I was looking for. I have a 10.04 LTS server I installed on a RAID-1 array. And I essentially want to un-RAID it back to a single disk because it is a VM (good news) and will be hosted on a RAID-5 host.

So, let me see if I understand it:
[LIST=1]
[*]Boot to Live CD
[*]stop md
[*]fail drives
[*]md remove from array
[/LIST]

Then what exactly? I assume I need to do something so GRUB will know to boot to the new disk.

My other option is I have clonezilla available. I am sure it will see just the individual drives, I could copy it, and create a new VM from that to play with.

---

### Post by rubylaser on 2011-03-28
I you want to be safe, I'd suggest going the Clonezilla route just to be safe.  But, what I posted earlier is fine. You should just need to get the UUID from blkid in a livecd. Then boot and enter that UUID, and finally run update-grub.

I have never personally done this procedure though, so that's why I recommended testing in a VM first.

---

### Post by ScottEChapman on 2011-03-28
Yea, I am pretty sure I can clone one of the drives. That would give me a new VM one a single drive, thus a broken RAID.

I could then do the steps outlined above and test them. But to be clear I would need to:
[LIST=1]
[*]install mdadm
[*]zero out the super block
[*]remove mdadm.conf from the drive
[*]Discover the UUID for the drive (not sure how to do that)
[*]update fstab to mount bu UUID (no sure what that would look like)
[*]run update-grub (not sure how to do that either)
[/LIST]

Sorry if I need more details, not all that experienced in this particular area...

Also, it sounds like some of the steps above are done when booted from the live CD, and than others from the disk itself?

---

### Post by rubylaser on 2011-03-28
> **ScottEChapman said:**
> Yea, I am pretty sure I can clone one of the drives. That would give me a new VM one a single drive, thus a broken RAID.

I could then do the steps outlined above and test them. But to be clear I would need to:
[LIST=1]
[*]install mdadm
[*]zero out the super block
[*]remove mdadm.conf from the drive
[*]Discover the UUID for the drive (not sure how to do that)
[*]update fstab to mount bu UUID (no sure what that would look like)
[*]run update-grub (not sure how to do that either)
[/LIST]

Sorry if I need more details, not all that experienced in this particular area...

Also, it sounds like some of the steps above are done when booted from the live CD, and than others from the disk itself?

livecd steps:
1. install mdadm
2. zero superblocks
3. get UUID for hard drive, here's the command...
 ```
blkid
```
4. The fstab would look like your current setup, but with the UUID swapped for the one you got above.
5. update-grub is the command to run :)

---

### Post by ScottEChapman on 2011-03-28
(sorry for the stupid question) but ALL the steps would be run from the live-cd? I would have expected update-grub after the system reboots.

I am also guessing that somehow I will be able to get it booted to the new disk in order to be able to run update-grub?

---

### Post by rubylaser on 2011-03-28
Yes, update-grub isn't from the livecd, you'll need to do that on the running system, sorry for the confusion.

---

### Post by ytotk on 2011-11-02
I am also trying to elegantly dissolve an os boot mirror into individual autonomous drives... Why does rubylaser recommend to make the changes thru a livecd? Why does /etc/fstab require changing to UUID instead of ie /dev/sda1?

---

### Post by rubylaser on 2011-11-02
> **ytotk said:**
> I am also trying to elegantly dissolve an os boot mirror into individual autonomous drives... Why does rubylaser recommend to make the changes thru a livecd? Why does /etc/fstab require changing to UUID instead of ie /dev/sda1?
Are you asking someone else why I would suggest a livecd, or would you like me to answer? ;)

If this is a running RAID1 that hosts your OS, you'll have to do this from a livecd because files will be in use , so it's a much safer/easier way to protect your data.

[This site]("http://www.unixtutorial.org/2008/05/ubuntu-uuid-how-to/") answers your UUID question.

---

### Post by darkod on 2011-11-02
> **ytotk said:**
> I am also trying to elegantly dissolve an os boot mirror into individual autonomous drives... Why does rubylaser recommend to make the changes thru a livecd? Why does /etc/fstab require changing to UUID instead of ie /dev/sda1?

1. The steps are run from a livecd because you can not stop the array if the OS is running from it while it's booted. Livecd will not boot from your disks so you can work on your array.

2. Yes, you can use /dev/sda1 in /etc/fstab, just make sure the disk is /dev/sda and not another letter.

3. I wonder if a further step is needed, to let grub know where exactly it needs to boot from after you break the array and you leave just one disk running. Something similar to recovering a lost grub bootloader (running from livecd):

sudo mount /dev/sda1 /mnt (mount your root partition)
sudo mount /dev/sda2 /mnt/boot (if you have separate /boot partition, if not skip this)
sudo grub-install --root-directory=/mnt /dev/sda (installing grub on the MBR of /dev/sda and telling it that the root partition is at /mnt where you mounted it)

If that doesn't boot right away you might need to chroot into the root partition to execute update-grub. Otherwise it needs to run at least once successfully in order to execute update-grub in the booted system.

---

