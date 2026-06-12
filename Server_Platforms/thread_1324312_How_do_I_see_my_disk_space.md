---
title: "How do I see my disk space?"
date: 2009-11-12
forum: Server Platforms
---

### Post by Cams on 2009-11-12
I just installed Karmic Koala server in order to serve audio files to my Squeeboxes. I've used Google and been able to install Squeezebox Server and actually got it working! 

I did the guided install with LVM. My computer has three physical drives. When I installed Squeezebox Server it asked where my media was stored and showed me an image of all the directories. I've attached that image to this post. 

I also found a tutorial about how to edit smb.conf to share directories on my Windows PC and that's working too. The final thing to do is to get my audio files onto the server. 

Ideally, I'd have all my files stored in /home/$username$/audio. I've created the audio folder and made $username$ sharable in Windows. Two things:

1. How do I view the available disk space?
2. How do I make the free space on all drives available for storing audio? Can I have all the disk space usable within /home/$username$/audio? I have some idea of how symbolic links work but I really could use some guidance on how to complete my set up. 

Please somebody, I need help! 

Thanks
Cams

---

### Post by CharlesA on 2009-11-12
You can check disk space used using:
```
df -h
```

In a terminal.

If you want to have the files stored in /home/$username$/audio on another drive, you'd have to mount that folder to the other drive.

---

### Post by Cams on 2009-11-12
Thanks. I've got the following:

```

Filesystem		Size	Used	Avail	Use%	Mounted on /dev/mapper/ubuntu-root
		366G	1.5G	346G	1%	/
udev		123M	200K	123M	1%	/dev
none		123M	0	123M	0%	/dev/shm
none		123M	496K	122M	1%	/var/run
none		123M	0	123M	0%	/var/lock
none		123M	0	123M	0%	/lib/init/rw
/dev/sda5	228M	14M	202M	7%	/boot

```

I have three IDE drives so I'm expecting to see hda, hdb and hdc, is that right? And where is /home/ located? 

You mentioned mounting /home/audio/ to another drive. How would I do that? And how could I pool the free space on disks 1, 2 and 3 for storage? Would I have to use the free space on disk 1 and then add a symbolic link to a folder on disk 2 and a folder on disk 3?

When I was using ClarkConnect 3.2, I could view the disk space on a web browser and I could use Webmin to administer it. Is there nothing like that on Ubuntu server?

I feel so close to getting this done and I dearly appreciate your help. 

thanks

---

### Post by karlson on 2009-11-12
> **Cams said:**
> 
I have three IDE drives so I'm expecting to see hda, hdb and hdc, is that right? And where is /home/ located? 


No that's not right.  You will see partitions on those drives if they are mounted as filesystems.  You may want to check /etc/fstab to see what's mounted.

If you want to see what drives you have on the system do:

```

sudo fdisk -l

```

> 
You mentioned mounting /home/audio/ to another drive. How would I do that?

By Adding an entry to /etc/fstab file.

>  And how could I pool the free space on disks 1, 2 and 3 for storage? Would I have to use the free space on disk 1 and then add a symbolic link to a folder on disk 2 and a folder on disk 3?


Use mdadm to create a raid array and then mount the new volume as a /home/audio or any other path.


> 
When I was using ClarkConnect 3.2, I could view the disk space on a web browser and I could use Webmin to administer it. Is there nothing like that on Ubuntu server?


Just a suggestion: Command line is your best friend in case of problems.

Webmin and other tools are nice, but if you're off the network and without a GUI is a bigger problem then it's worth.

---

### Post by MaxIBoy on 2009-11-12
It appears that you have no home partiton, in which case /home is just a folder within root ("/"). 

A mount point is always a directory. If the directory is not empty, then when you mount over it its contents become invisible until you unmount it.

You can mount any filesystem to any mount pont. Just use 
```
sudo mount -t TYPE_OF_FILESYSTEM /dev/device /location/of/mountpoint
```
So on my laptop (where my username is maxtothemax,) if I were to create an EXT4 formatted /dev/sda5 partition for music, the command would be 
```
sudo mount -t ext4 /dev/sda5 /home/maxtothemax/music
```If, in this example, I would like to make this happen automatically at boot, edit the file /etc/fstab and add an appropriate entry like this:
```
/dev/sda4    /home/maxtothemax/music    ext4     noatime     0     0
```The noatime option improves performance a lot, but the records of when files were last updated won't be accurate down to the second. If that info is important to you, substitute defaults instead of noatime. The noatime option is only for EXT filesystems.

---

### Post by Cams on 2009-11-12
Thanks for such a speedy response. I understand that the command line is my friend, but when I'm sat there looking at a blinking cursor I have no idea what commands to enter to do anything. So far I'm feeling quite pleased at what I've been able to find with regards to getting Squeezebox Server installed and actually working. 

> Use mdadm to create a raid array and then mount the new volume as a /home/audio or any other path.

Is there a tutorial that you know of for explaining how to do this? In fact I'm not really sure how to edit fstab or what to do with it. Having found instructions for changing smb.conf, I guess I could follow those instructions again, i.e. use vim, insert and :wq to edit fstab, but what would I put there? 

Following my last post, I downloaded and booted gparted and now I can see that indeed I do have /dev/hda, /dev/hdb and /dev/hdc. hda has the following partitions:

```

Partition	Filesystem	Size		Used		Unused
hda1		lvm2		372.37 GB	--		--
hda2		extended	243.17 MB	--		--
hda5		ext2		243.14 MB	29.21 MB	213.21 MB

```

/dev/hdb and /dev/hdc are both unallocated. I guess that means that they must be formatted? That seems easy enough to do in gparted, but I guess I should be learning the command line and documenting that. What filesystem should be used and how does one do it from the command line? 

You know what I'm trying to achieve, basically to get as much free disk space as I can pooled for storing audio files. I've never used RAID before so that's new territory for me.

Thanks once again. I'm off to put the kids to bed now and I'll no doubt be burning the midnight oil again tonight trying to get this done and dusted! I could not do it without the help I get here and I thank you once again.

---

### Post by CharlesA on 2009-11-12
Not sure what is going on with those 2 drives. Try seeing what partitions are on them with gparted.

Also howto on mdadm: [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by Cams on 2009-11-12
Okay, looks like I'm getting somewhere. I think the sensible thing to do would be to create a partition on each of the two 250 GB drives (hdb and hdc) that spans the entire drive, then use mdadm to make a raid array out of them. From the tutorial that you linked to Charles, it looks like I'm taking the manual route. What filesystem would make the most sense for the partitions? I think I'll just create the partitions in gparted as it's a lot more intuitive. Unless someone would like to explain how to do it from the command line?

---

### Post by Cams on 2009-11-12
Just one other thing. It would appear from what I can see using df -h and gparted that I have no swap partition. Is this something that I need? Or do I have it already? If not, should I create swap partitions on each of the other two drives before using mdadm?

---

### Post by CharlesA on 2009-11-12
I wonder what happened to the swap partition.

This [FAQ]("https://help.ubuntu.com/community/SwapFaq") might help in regards to the swap question, but I don't know for sure.

I haven't use mdadm before, but when I set my hardware array up, I just partitioned everything as EXT3 and use the RAID management software to set up the array. I think the same thing happens with mdamd.

---

### Post by Cams on 2009-11-12
> **CharlesA said:**
> This [FAQ]("https://help.ubuntu.com/community/SwapFaq") might help in regards to the swap question, but I don't know for sure.

Nice linkage! I just followed the instructions for creating a swap file and it seems to have worked. Not sure why the default installer didn't do it but there you go; I've got one now. 

I'll create two partitions now, one on each of the two 250 GB drives and then try to software RAID them with the instructions. Wish me luck!

---

### Post by Cams on 2009-11-12
Should the new partitions on the bare HDDs be Primary Partitions or Extended? These are the ones I'll be using to work with mdadm to create a RAID 0 array.

---

### Post by MaxIBoy on 2009-11-12
> **Cams said:**
> Should the new partitions on the bare HDDs be Primary Partitions or Extended? These are the ones I'll be using to work with mdadm to create a RAID 0 array.Extended partitions would be if you are creating sub-partitions within them. If your plan is to *join* partitions, that's probably a bad thing to do.

---

### Post by Cams on 2009-11-13
I ended up nowhere last night. I did the mdadm thing and managed to create a 500 GB RAID 0 on the two physical HDDs but they disappeared after reboot. 

Long story short, I've reinstalled the whole thing and tried using the RAID configuration tool at the install. After reinstall, I have:

```

Filesystem		Size	Used	Avail	Use%	Mounted on /dev/sda1
		92G	2.0G	86G	3%	/
udev		123M	208K	123M	1%	/dev
none		123M	0	123M	0%	/dev/shm
none		123M	528K	122M	1%	/var/run
none		123M	0	123M	0%	/var/lock
none		123M	0	123M	0%	/lib/init/rw

```

sudo fdisk -l shows that I have:

```
dev/sdc: 250.1 GB
/dev/sdc1 - Start - 1 End - 30401 - Blocks - 244196001 - System - Linux RAID autodetect

dev/sdb: 250.1 GB
/dev/sdb1 - Start - 1 End - 30401 - Blocks - 244196001 - System - Linux RAID autodetect

Disk /dev/md0: 500.1 GB
/dev/md0p1 - Start - 1 End - 30401 - Blocks - 244196001 - System - Linux RAID autodetect
```

I can't see /dev/sda. I think it scrolled off the top of the screen. 

/dev/md0 is I think what was created when I did the manual mdadm RAID creation last night. It was still visible in the partiiton tool at the beginning of the manual install process today and I couldn't get rid of it. 

I'm not sure what I've done or how to check where the disk space is. /dev/sda should be 400 GB and it's the disk I've used for the install files. So what I'm looking for is to RAID 0 the two 250 GB drives into one 500 GB volume, or, even better, do that AND use some of the free space on the 400 GB drive to make a bigger volume. 

I was up until after 1.30am last night and had a helluva day today because I was really tired and my staff were ALL off sick. And now I'm starting again and am worried I'll be up late again tonight. Is this how Linux is? Don't get me wrong, I am quite geeky and enjoy learning this stuff, but it's a STEEP curve and all I want is to get this done so I can start packing for leaving on my holidays on Sunday.

Can anyone PLEASE help?!

---

### Post by CharlesA on 2009-11-15
I don't know if it'll help but check this out: [http://ubuntuforums.org/showthread.php?t=884556](http://ubuntuforums.org/showthread.php?t=884556)

---

### Post by Cams on 2009-11-15
That helped! I used the md0 partition that was still around from before the install. I now have all my music files back on the server, so in two places (phew!). I was so paranoid of drive failure with my audio files in only one place. Scary!

So now it's done, my bags are packed and I'm off on holiday for two weeks! When I get back, my server will be all working and good. 

Ubuntu server seems nice.

---

### Post by CharlesA on 2009-11-15
Glad it working now! Enjoy yer holiday! :D

---

