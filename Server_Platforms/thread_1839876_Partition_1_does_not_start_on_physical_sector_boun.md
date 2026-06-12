---
title: "Partition 1 does not start on physical sector boundary."
date: 2011-09-06
forum: Server Platforms
---

### Post by davidmaxwaterman on 2011-09-06
I'm trying to prepare 3 disks for a RAID5, but I get the above when trying to create the partition on two of the disks - the other one is fine.

sdc does not produce the error, but sd[de] produce the error. See below for fdisk -l output. I previously had them in an array as whole disks, but I screwed it up so now I need to restore from backup, but I want to create the new array 'correctly'.

I read an FAQ that said that I need to upgrade to a newer fdisk, but where can I get it from?

Thanks,

Max.

11.04.

```
root@jeeves:~# fdisk -l /dev/sd[cde]

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00098452

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000ca99c

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00028409

   Device Boot      Start         End      Blocks   Id  System
root@jeeves:~# 

```

---

### Post by davidmaxwaterman on 2011-09-07
No one knows how to fix this issue? Perhaps someone has a recommendation for where best to ask?

---

### Post by YesWeCan on 2011-09-07
Hey hows it going? Tumbleweed blowing through the thread? :)
Do you want to erase all 3 disks and reformat them from scratch...you have everything backed up, right?

I'd suggest

```
sudo dd if=/dev/zero of=/dev/sdx bs=1M count=100 conv=notrunc,noerror
```
repeat for each drive

Use **Disk Utility** to "format drive" and give each one a new MBR.
Then "File", "Create" and have it make a RAID 5 for you:
512 stripe size
Give it a name (but do not use spaces or it screws up the mdadm.conf!)
Select the 3 drives
Then where the array size slider is, at the right is a box with the size. Round it down to the nearest 0.1GB by editing the number. Eg: If it says 2000.123GB then change it to 2000.1GB.
Then set it going.

It will give it an arbitrary device name that is not being used, /dev/mdN
Click on the RAID device icon on the left and then the partition in the graphic and then "Format Volume".

Finally, add the ARRAY directive to mdadm.conf.
```
sudo mdadm -Ds
```
copy the line for the new RAID to mdadm.conf and change the device name to /dev/md? as you wish.
Delete or comment out the old RAID5 one.

Stop the array and reassemble it to make sure mdadm.conf is right
```
mdadm --stop /dev/mdN  [COLOR="DimGray"](its current name)[/COLOR]
```
```
mdadm -As
```
check it reports assembling it with the device name you specified in mdadm.conf

edit fstab to mount it at boot with its new device name and then
```
sudo mount -a
```
and check it is correctly mounted

Once all is ok,
```
sudo update-initramfs -u
```

---

### Post by davidmaxwaterman on 2011-09-08
> **YesWeCan said:**
> Hey hows it going?


so so. I lost all of my raid5 array :/ I thought it'd be a simple matter to "make a new one", but no :/

>  Tumbleweed blowing through the thread? :)


Yeah :/

> 
Do you want to erase all 3 disks and reformat them from scratch...you have everything backed up, right?


What I have backed up, is what I have backed up. I am forced to make use of it now since the array is toast.

> 
I'd suggest

```
sudo dd if=/dev/zero of=/dev/sdx bs=1M count=100 conv=notrunc,noerror
```
repeat for each drive

Use **Disk Utility** to "format drive" and give each one a new MBR.
Then "File", "Create" and have it make a RAID 5 for you:
512 stripe size
Give it a name (but do not use spaces or it screws up the mdadm.conf!)
Select the 3 drives
Then where the array size slider is, at the right is a box with the size. Round it down to the nearest 0.1GB by editing the number. Eg: If it says 2000.123GB then change it to 2000.1GB.
Then set it going.

It will give it an arbitrary device name that is not being used, /dev/mdN
Click on the RAID device icon on the left and then the partition in the graphic and then "Format Volume".

Finally, add the ARRAY directive to mdadm.conf.
```
sudo mdadm -Ds
```
copy the line for the new RAID to mdadm.conf and change the device name to /dev/md? as you wish.
Delete or comment out the old RAID5 one.

Stop the array and reassemble it to make sure mdadm.conf is right
```
mdadm --stop /dev/mdN  [COLOR="DimGray"](its current name)[/COLOR]
```
```
mdadm -As
```
check it reports assembling it with the device name you specified in mdadm.conf

edit fstab to mount it at boot with its new device name and then
```
sudo mount -a
```
and check it is correctly mounted

Once all is ok,
```
sudo update-initramfs -u
```

ok :) sounds like a plan...I'll get right to it this evening when I get home. Thanks for the detailed instructions!

Max.

---

### Post by CharlesA on 2011-09-08
I've had the same thing happen with my 3TB external (4096 byte sectors). It's a problem with fdisk and the advanced format disks.

---

### Post by davidmaxwaterman on 2011-09-08
> **CharlesA said:**
> I've had the same thing happen with my 3TB external (4096 byte sectors). It's a problem with fdisk and the advanced format disks.

and your solutions was...

---

### Post by Grenage on 2011-09-09
I know that gparted now has the option to correctly handle 4k; I *thought* that the current Ubuntu fdisk release also did - guess not!

Would setting the start sector as 64 ( divisible by 8 ) not achieve correct alignment?  I assume that formatting to 4096 size would also be recommended?

---

### Post by CharlesA on 2011-09-09
> **davidmaxwaterman said:**
> and your solutions was...

Ignore it, gparted/parted said everything was fine. I ended up having to use the 10.10 version instead of 10.04 of parted/gparted tho (live cd ftw)

> **Grenage said:**
> I know that gparted now has the option to correctly handle 4k; I *thought* that the current Ubuntu fdisk release also did - guess not!

Would setting the start sector as 64 ( divisible by 8 ) not achieve correct alignment?  I assume that formatting to 4096 size would also be recommended?

When I used gparted, it correctly aligned the partition, I don't think the version in 10.04 did tho, as I had to use 10.10 to get it working.

---

### Post by davidmaxwaterman on 2011-09-10
> **Grenage said:**
> I know that gparted now has the option to correctly handle 4k; I *thought* that the current Ubuntu fdisk release also did - guess not!

Would setting the start sector as 64 ( divisible by 8 ) not achieve correct alignment?  I assume that formatting to 4096 size would also be recommended?

well, i took your hint and went one better....i started the partition at 8 (also divisible by 8). seemed to work ok.

i'm now wondering how best to test the file system i've put on top of it.

i'm usind 'dd' to make a huge file, to see if i get any i/o errors...any other ideas?

---

### Post by YesWeCan on 2011-09-10
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-lnxw074KB-Disksdth-LX](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-lnxw074KB-Disksdth-LX)

I'm confused now. On an MBR format the first sector of the first partition is not supposed to start before 63. I'm surprised you were able to start a partition at 8. What tool did you use? Traditionally 63 is partition 1 start and now Windows tends to start it at 2048.

Starting before 63 will create a problem for Grub because it needs this gap to embed itself. Not a concern in this case because I assme this RAID will not be used for booting.


You might want to run e2fsck for peace of mind.

---

### Post by davidmaxwaterman on 2011-09-10
> **YesWeCan said:**
> [http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-lnxw074KB-Disksdth-LX](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html?ca=dgr-lnxw074KB-Disksdth-LX)

I'm confused now. On an MBR format the first sector of the first partition is not supposed to start before 63. I'm surprised you were able to start a partition at 8. What tool did you use? Traditionally 63 is partition 1 start and now Windows tends to start it at 2048.

Starting before 63 will create a problem for Grub because it needs this gap to embed itself. Not a concern in this case because I assme this RAID will not be used for booting.


You might want to run e2fsck for peace of mind.

hrm...well, when it created the partitions without me specifying values, it chose '1', so I guessed '8' would be fine. i was using fdisk and it didn't complain and disk utility doesn't show any warning either.

i was previously using the whole disk so i don't see why i need to leave any space...

---

### Post by YesWeCan on 2011-09-10
If it were me I'd start at 64 just to avoid tempting the gods. ;)

You could be daring by formatting ext4 with 4096 byte block size as Grenage suggested.

I'm not sure how mkfs.ext4 decides what block size to choose. You can see this and all the superblock info using dumpe2fs -h

---

### Post by davidmaxwaterman on 2011-09-10
> **YesWeCan said:**
> If it were me I'd start at 64 just to avoid tempting the gods. ;)

You could be daring by formatting ext4 with 4096 byte block size as Grenage suggested.

well, i am using xfs and it seems to use 4096 blocks already...why is it 'daring'?

i've repartitioned to start at 64 using gpartd (don't like the gui :(), and it seemed to work ok. filling the disk now to see if i get any i/o errors, which is what i think happens when the filesystem is too big for the device...or something.

---

### Post by YesWeCan on 2011-09-10
On my system ext4 defaulted to 1024. So 4096 may be less common. I dont know.
Why XFS?
In any case, mdadm will replace the underlying format so it is not necessary to preformat the partitions. But I realise you are doing this to check the drive integrity.

---

### Post by davidmaxwaterman on 2011-09-10
> **YesWeCan said:**
> On my system ext4 defaulted to 1024. So 4096 may be less common. I dont know.
Why XFS?

I have SGI heritage and have learned to trust it :)
> 
In any case, mdadm will replace the underlying format so it is not necessary to preformat the partitions. But I realise you are doing this to check the drive integrity.

Well, it seems to be ok now, but now it's starting to build this as md127...again (though it was a different array before).

Max.

---

### Post by YesWeCan on 2011-09-10
I lied. My ext4 on mdraid defaults to 4096 bytes per block. :)
It defaulted to 1024 on a non-raid disk partition I created in VBox.

You need an entry in mdadm.conf to assign a different name to the array.

---

### Post by N1XRR on 2011-10-21
In case anyone else is having this issue...

I'm using a 3TB drive also, giving me the same error: "Partition 1 does not start on physical sector boundary."

I tried bumping the beginning cylinder to 1,8,16,64 but I kept getting the same thing.

What I did to fix the issue was use the 'c' command and then 'u' command when I entered fdisk.  This turns off DOS compatibility and changes fdisk to address sectors instead of cylinders (I think).  Anyway, now using the new command and using defaults works perfectly fine.

-Mike

---

### Post by studout on 2011-10-27
N1XRR; Thank you!  :)

---

### Post by krushmoto on 2012-06-26
> **N1XRR said:**
> In case anyone else is having this issue...

I'm using a 3TB drive also, giving me the same error: "Partition 1 does not start on physical sector boundary."

I tried bumping the beginning cylinder to 1,8,16,64 but I kept getting the same thing.

What I did to fix the issue was use the 'c' command and then 'u' command when I entered fdisk.  This turns off DOS compatibility and changes fdisk to address sectors instead of cylinders (I think).  Anyway, now using the new command and using defaults works perfectly fine.

-Mike

Hi Mike,
I'm having the same problem you had and am new to Ubuntu and Linux.  Can you dumb it down for me and explain what I need to do in fdisk?  I have DOS knowledge.
Thanks.

---

### Post by CharlesA on 2012-06-26
Don't use fdisk for partitioning. Use gparted or regular parted if you don't want to use a GUI.

gparted is on the ubuntu livecd.

---

### Post by krushmoto on 2012-06-26
> **CharlesA said:**
> Don't use fdisk for partitioning. Use gparted or regular parted if you don't want to use a GUI.

gparted is on the ubuntu livecd.

Thanks for the info Charles.  Seems more user friendly.  Now for the stupid question:
What do I set everything to?  
It's a 2TB HD that I'm planning on swapping out in a WD My Book Home Edition.  It came with a 500GB HD but plan on swapping it out with this one.  I checked the existing HD and it's a 500GB formatted in NTFS.
Any help anyone can provide I'd really appreciate it.
Thanks.

---

### Post by CharlesA on 2012-06-26
If you are going to use it with Windows, format it as NTFS, otherwise ext4 would work wonders if you are going to use it for Linux only.

---

### Post by krushmoto on 2012-06-26
> **CharlesA said:**
> If you are going to use it with Windows, format it as NTFS, otherwise ext4 would work wonders if you are going to use it for Linux only.

Thanks Charles.
I appreciate the info!

---

### Post by lovevn on 2012-09-16
Hi everyone.
I'a having an similar mistake. I try mount a file .iso to listen by 
```
sudo mount -o loop /home/x.iso /media
```
but it's not fortunate,  I'm wrong, so when I type
```
sudo fdisk -l
``` it likes this:
[IMG]http://http://ubuntuforums.org/attachment.php?attachmentid=224231&stc=1&d=1347804450[/IMG]
What was happened? What can I do to fix? Help me, please!

---

### Post by jasmines on 2013-03-03
[http://askubuntu.com/q/156994/32230](http://askubuntu.com/q/156994/32230)

---

