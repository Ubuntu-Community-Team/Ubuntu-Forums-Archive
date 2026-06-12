---
title: "SnapRAID &amp; AUFS Permissions - Doing it right?"
date: 2013-09-23
forum: Server Platforms
---

### Post by mark56 on 2013-09-23
Hi,

I'd had issues with mdadm and my RAID array that a forum member helped me through here: [http://ubuntuforums.org/showthread.php?t=2174124](http://ubuntuforums.org/showthread.php?t=2174124)
As such, he recommended a tutorial that Rubylaser posted on his site to setup SnapRAID & AUFS, especially since running a server for a Media Center.

I have since rebuilt my server over the weekend, and followed Rubylasers tutorial [http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04](http://zackreed.me/articles/72-snapraid-on-ubuntu-12-04), but when trying to create folders in /storage as my own user account, am unable to do so.
I chown & chgrp /storage to mark:mark vs root:root and finally chmod the /storage folder to 777.  I still couldn't create/do anything in there.  

As root, I created a /storage/Media folder, and set it to mark:mark, and my user account has full access to do everything in there, so I'm not overly concerned about it, but is that expected behavior?  

A second question... once all of my data has completed it's move, I'd like to grow the "array" with those drives.  What steps do you make to grow the SnapRAID array?  

Thanks,
Mark

---

### Post by rubylaser on 2013-09-23
Hello, I'm glad that you found some of my tutorials to be helpful.  I'll be happy to try to help you out :)  I would bet that your underlying drives don't have permissions allowing the user to write to the directories.  Remember, AUFS is an overlaying filesystem that presents the original filesystems as one logical volume.  If you followed my tutorial, your disks should be mounted in /media.  Change into your /media directory, and chown / chmod the original disks like this.

```
sudo -i
cd /media
chmod -R 755
chown -R user:group /media/mountpoints

```

mine look like this
```

root@fileserver:/media# ls -latotal 56
drwxr-xr-x 14 zack zack 4096 Jul 28 08:38 .
drwxr-xr-x 24 root root 4096 Sep  9 14:19 ..
drwxrwxrwx 11 zack zack 4096 Jul 28 08:30 HIT-ML0220F30YYYXD
drwxrwxrwx  2 zack zack 4096 Jun 28 18:39 HIT-ML4220F3156XYK
drwxrwxrwx 11 zack zack 4096 Jul 28 08:30 SEA-5XW0M4T1
drwxrwxrwx 11 zack zack 4096 Sep 22 23:05 SEA-5YD1779C
drwxrwxrwx 12 zack zack 4096 Sep 22 23:05 SEA-5YD2W98N
drwxrwxrwx 13 zack zack 4096 Sep 22 23:05 SEA-5YD6N2GA
drwxrwxrwx 13 zack zack 4096 Jul 31 18:22 SEA-6YD0ZX2E
drwxrwxrwx 15 zack zack 4096 Jul 28 08:30 SEA-6YD1PM58
drwxrwxrwx  3 zack zack 4096 Sep 14 16:32 SEA-6YD1R3YF
drwxrwxrwx  3 zack zack 4096 Jul 11 17:51 SEA-Z3100AN3

```

In regards to adding a new disk, this is also really easy.  Just partition the new disk, add a filesystem to the disk, create a mountpoint for the new filesystem, and add it to /etc/fstab.  Next, you need to add the new disk to /etc/snapraid.conf, and run snapraid sync. Finally, you need to modify your AUFS mount command and add your new disk.  After writing all of this it seems like a lot of steps, but it really only takes a couple minutes to add another disk.  Let me know if you have other questions.

---

### Post by mark56 on 2013-09-23
Well that sounds about right actually.  I'll check it out when I get home, but I'm pretty sure that'll do it.

And to be honest, that sounds easy enough to add a disk.  Sounds pretty much like following the prior steps for setting it up, just appending to what's already there.  Cool... I appreciate it.

---

### Post by mark56 on 2013-10-04
Ok, I have another question... and honestly, I think this is self explanatory at this point, but thought I'd ask.  

I have 6 SATA ports on my mobo.  I have two addon controller cards, 1 with 4 ports and 1 with 2 ports.  I'd like to have my parity drives on the addon cards.  If the mobo fails, then really all the data still exists. If the addon card fails, the array is fine, but the parity drives just need to be moved and setup on another controller.  Basically, in my head, that makes sense.  It would also suggest that all 5 drives I anticipate on being part of the array (not parity drives) would be on the same controller, thus having better performance than putting any onto an addon card?  

So, if that all sounds decent, do i just add the new parity drives on the addon card, and setup the configurations, then format the current parity drive and then add that to the array as a data drive?  

Am I overthinking things?

---

### Post by rubylaser on 2013-10-04
I wouldn't expect any better perform from one card to another, other than if one is hooked up to an old PCI bus vs. PCI Express. Also, you can move your disks to a new controller without needing to format them if you have set them up in /etc/fstab to mount by their UUID.

As a side note: If you have an open PCIe x8 or x16, I would suggest you get a decent HBA that supports 8 hard drives attached to it.  I use one of these [IBM m1015]("http://www.ebay.com/itm/IBM-ServeRaid-M1015-PCI-e-RAID-Controller-Full-Height-Bracket-46M0861-46C8933-/200963939801?pt=US_Server_Disk_Controllers_RAID_Cards&hash=item2eca625dd9") flashed to as an LSI 9211-8I in IT mode.

---

### Post by mark56 on 2013-10-07
Thanks again.  I'm not sure I've done this right, but I've added another data drive, and another parity drive using the q-parity option in snapraid.conf.  I'm running a snapraid fix right now, and it's scrolling tons of data error/fix data error.  Is it supposed to do that?  

```
Reading missing data from file '/media/WD-WMC4N0439362/snapraid.q-parity' at offset 4740349952.error:18083:q-parity: Read error
fixed:18083:q-parity: Fixed data error
Reading missing data from file '/media/WD-WMC4N0439362/snapraid.q-parity' at offset 4740612096.
error:18084:q-parity: Read error
fixed:18084:q-parity: Fixed data error
Reading missing data from file '/media/WD-WMC4N0439362/snapraid.q-parity' at offset 4740874240.
error:18085:q-parity: Read error

```

I killed that one, and started it up again, and the errors now scroll and read as such:

```

error:140314:q-parity: Data error
fixed:140314:q-parity: Fixed data error
error:140315:q-parity: Data error
fixed:140315:q-parity: Fixed data error
error:140316:q-parity: Data error
fixed:140316:q-parity: Fixed data error
error:140317:q-parity: Data error
fixed:140317:q-parity: Fixed data error

```

these are the updates I made:
Snapraid.conf
```

parity /media/WD-WMC1T2501603/snapraid.parity
**q-parity /media/WD-WMC4N0439362/snapraid.q-parity**


content /var/snapraid/content
content /media/WD-WMC1T2600294/content
content /media/WD-WMC1T2561550/content


disk d1 /media/WD-WMC1T2561550
disk d2 /media/WD-WMC1T2600294
disk d3 /media/WD-WCC1T0877796
**disk d4 /media/WD-WMC4N0455643**

```

fstab
```

# SnapRAID Disks
UUID=4183b1ce-2fb9-44d4-9914-b6a6b0e367a9 /media/WD-WMC1T2600294 ext4 defaults 0 2
UUID=bbe2edd6-a932-4156-aabf-bb259f4a3ba9 /media/WD-WCC1T0877796 ext4 defaults 0 2
UUID=7d732b73-b482-4543-afab-4d1d326f01d2 /media/WD-WMC1T2561550 ext4 defaults 0 2
**UUID=2731285b-c526-404c-98ac-8f3e63b4a5a6 /media/WD-WMC4N0455643 ext4 defaults 0 2**


# Parity Disks
UUID=ce0a7114-ca2f-453d-a025-4bd57bd486a9 /media/WD-WMC1T2501603 ext4 defaults 0 2
**UUID=5b614d18-df0b-4a36-b5a7-5a06e9128173 /media/WD-WMC4N0439362 ext4 defaults 0 2**

```


So I guess... does it look like I'm doing things right?  Are those errors normal with the "fix"?

---

### Post by mark56 on 2013-10-08
So I let it run overnight, and it's still going scrolling the same stuff... except it's up in the 8700000 range now.  Man, I sure hope I'm doing this right. LOL

```
error:140314:q-parity: Data errorfixed:140314:q-parity: Fixed data error
error:140315:q-parity: Data error
fixed:140315:q-parity: Fixed data error
error:140316:q-parity: Data error
fixed:140316:q-parity: Fixed data error
error:140317:q-parity: Data error
fixed:140317:q-parity: Fixed data error
```

---

### Post by mark56 on 2013-10-08
Ok, it finally finished.  Where /dev/sdg1 is the q-parity.  According to this, it looks like it's taking an appropriate amount of space?  Do I just trust that it's setup right, or is there a way to know it's right?

```

[FONT=arial]fixed:9497587:q-parity: Fixed data error[/FONT]
[FONT=arial]100% completed, 7107409 MiB processed[/FONT]
[FONT=arial]9480053 read/data errors[/FONT]
[FONT=arial]9480049 recovered errors[/FONT]
[FONT=arial]2 UNRECOVERABLE errors[/FONT]
[FONT=arial]root@MediaMaster:/media# df -h[/FONT]
[FONT=arial]Filesystem                        Size  Used Avail Use% Mounted on[/FONT]
[FONT=arial]/dev/mapper/MediaMaster--vg-root  222G  6.3G  204G   3% /[/FONT]
[FONT=arial]udev                              3.9G  8.0K  3.9G   1% /dev[/FONT]
[FONT=arial]tmpfs                             1.6G  1.2M  1.6G   1% /run[/FONT]
[FONT=arial]none                              5.0M     0  5.0M   0% /run/lock[/FONT]
[FONT=arial]none                              3.9G  212K  3.9G   1% /run/shm[/FONT]
[FONT=arial]/dev/sda1                         228M   68M  148M  32% /boot[/FONT]
[FONT=arial]/dev/sdb1                         2.7T  2.3T  292G  89% /media/WD-WMC1T2501603[/FONT]
[FONT=arial]/dev/sdc1                         2.7T  2.3T  299G  89% /media/WD-WMC1T2561550[/FONT]
[FONT=arial]/dev/sdd1                         2.7T  2.3T  298G  89% /media/WD-WMC1T2600294[/FONT]
[FONT=arial]/dev/sde1                         2.7T  2.3T  298G  89% /media/WD-WCC1T0877796[/FONT]
[FONT=arial]none                              8.1T  6.8T  893G  89% /storage[/FONT]
[FONT=arial]/dev/sdf1                         2.7T   73M  2.6T   1% /media/WD-WMC4N0455643[/FONT]
[FONT=arial]/dev/sdg1                         2.7T  2.3T  292G  89% /media/WD-WMC4N0439362

```

The new data drive does not seem to have added to the array though.  So it seems I might have missed something there?  /dev/sdf1.  /storage is still the same size.  
I ran snapraid sync:

```

root@MediaMaster:/media# snapraid sync


Self test...
Loading state from /var/snapraid/content...
Scanning disk d1...
Scanning disk d2...
Scanning disk d3...
Scanning disk d4...
Using 1335 MiB of memory.
Saving state to /var/snapraid/content...
Saving state to /media/WD-WMC1T2600294/content...
Saving state to /media/WD-WMC1T2561550/content...
Initializing...
Syncing...
100% completed, 1666 MiB processed          
Saving state to /var/snapraid/content...
Saving state to /media/WD-WMC1T2600294/content...
Saving state to /media/WD-WMC1T2561550/content...
root@MediaMaster:/media# 

```

And while typing this, I seemed to figure it out, i had to umount then mount -a again, and voila, I have 11TB in /storage!  
Wow, I think I just talked myself through this?  LOL
[/FONT]

---

### Post by rubylaser on 2013-10-08
Great, I'm glad you got it figured out.  Everything looks good :)

---

### Post by mark56 on 2014-09-12
Hi rubylaser,

I wanted to hit you up here because I'm having a different issue, but it's my configuration above.  It seems my boot disk has gone bad.  I do not have a backup of my configs... but I followed your guide to the tee, and have my config lucky posted here.  
If I were to reload 12.04, what parts of your instructions do I change/do different to recover and use my existing SnapRAID configuration??  Since it's already there and created.  

Thanks,

Mark

---

### Post by mark56 on 2014-09-13
Well, it seems like I got it... figured out the obvious parts, such as not creating and copying drives and partitions... I did go from like Snapraid 3.2 to 6.3 (your current guide).  I also installed Ubuntu 14.04 Server instead of 12.04.  Once I got it all up and mounted though, I found I have LOTS of folders that I've either renamed or deleted some time ago.  I deleted them all, and SOME of them came back again, so I've deleted them again.  I'm guessing these are the "White Out" files??  They are just normal folder names, and they're all empty, so easy enough to sort by size in Dolphin, and remove, but hopefully they stay away??  

If I did want to try MHDDFS, do I have to recreate everything, or is it just simply bringing everything together with that filesystem instead?  Would I lose anything, or would I have to recreate anything?

Also, are there any tests or anything that I should run to ensure the array is good?  Had setup the SMART monitoring before, still need to do that.  It alerted me to my main drive dying, but it just went all out and died without mercy.

---

### Post by rubylaser on 2014-09-14
> **mark56 said:**
> Well, it seems like I got it... figured out the obvious parts, such as not creating and copying drives and partitions... I did go from like Snapraid 3.2 to 6.3 (your current guide).  I also installed Ubuntu 14.04 Server instead of 12.04.  Once I got it all up and mounted though, I found I have LOTS of folders that I've either renamed or deleted some time ago.  I deleted them all, and SOME of them came back again, so I've deleted them again.  I'm guessing these are the "White Out" files??  They are just normal folder names, and they're all empty, so easy enough to sort by size in Dolphin, and remove, but hopefully they stay away??  

If I did want to try MHDDFS, do I have to recreate everything, or is it just simply bringing everything together with that filesystem instead?  Would I lose anything, or would I have to recreate anything?

Also, are there any tests or anything that I should run to ensure the array is good?  Had setup the SMART monitoring before, still need to do that.  It alerted me to my main drive dying, but it just went all out and died without mercy.

I have moved away from AUFS for the reason of the annoying whiteout and opaque files. The good news is that it's super easy to transistion from AUFS to mhddfs.  All you do is umount your AUFS pool, install mhddfs, and then mount your pool with mhddfs in the same location.  This will allow samba or NFS shares to continue to work just like they did with AUFS.  I have a [post on my site]("http://zackreed.me/articles/84-snapraid-with-mhddfs") that covers mhddfs as well.

I would definitely setup smartmontools again, along with email alerts, and a UPS if you have one.  Other good ideas are using Clonezilla to make a clone of your OS drive once you get it setup how you like.  I also do a weekly rdiff-backup of my OS drive to an external hard drive.  That way, even if your OS drive takes a dump, you can be back up in working in the time it takes to Clone your backup onto your new drive.  Another option would be to use mdadm to make a RAID1 array out of your OS drive so you can survive a drive failure without the machine going down.  But, if you aren't used to mdadm, it's probably not worth your time if you have a good clone, and are doing routine backups.

Hope that helps :)  Also, if you have a question, it's easier for me if you post it on my site.  I get an email alert anytime someone posts a question.  When it's here on the forums, I have to hopefully stumble across it.

---

