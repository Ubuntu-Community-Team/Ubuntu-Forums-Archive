---
title: "RAID drive not mounting to specified mountpoint"
date: 2017-03-26
forum: Server Platforms
---

### Post by vrubel68 on 2017-03-26
Can anyone explain why my drives aren't mounting to the specified location in my /fstab?

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system>                <mount point>    <type>            <options>           <dump>  <pass>
proc                                       /proc            proc                nodev,noexec,nosuid  0      0  
# / was on /dev/sde1 during installation
UUID=5537ba8b-96f2-4c89-b913-65c06dc8ed96  /                ext4                noauto               0      1  
# swap was on /dev/sde5 during installation
UUID=7be7b09c-adfb-4415-b923-67a0a52b44b3  none             swap                sw                   0      0  

/dev/md0                                   /ext4        defaults                     0        0  
/dev/sdb1                                  /media/sdb1      linux_raid_member    defaults             0        0  
/dev/sdc1                                  /media/sdc1      linux_raid_member    defaults             0        0  
/dev/sdd1                                  /media/sdd1      linux_raid_member    defaults             0        0

```

This is causing the infamous "Not ready or not present" boot problem.

---

### Post by SeijiSensei on 2017-03-26
You shouldn't be mounting the individual components of the array.

Also the syntax for mounting  the array is incorrect.  I assume it has an ext4 filesystem., and  I doubt you have a mount point called /ext4.  Let's create one under /media and mount the array there for testing:
```

sudo mkdir /media/raid
sudo mount /dev/md0 /media/raid

```
If that works replace the entry in /etc/fstab with 
```
/dev/md0    /media/raid     ext4     defaults     0 0 
```

---

### Post by vrubel68 on 2017-03-26
> **SeijiSensei said:**
> You shouldn't be mounting the individual components of the array.

Also the syntax for mounting  the array is incorrect.  I assume it has an ext4 filesystem., and  I doubt you have a mount point called /ext4.  Let's create one under /media and mount the array there for testing:
```

sudo mkdir /media/raid
sudo mount /dev/md0 /media/raid

```
If that works replace the entry in /etc/fstab with 
```
/dev/md0    /media/raid     ext4     defaults     0 0 
```

I didn't think they were supposed to mount individually, but the drives didn't show up individually in the tree in 12.04 and it didn't seem to be more than a nuisance.

I created the directory and then tried to mount to it.

```

evocati@evocati-desktop:~$ sudo mkdir /media/raid
[sudo] password for evocati: 
evocati@evocati-desktop:~$ sudo mount /dev/md0 /media/raid
mount: special device /dev/md0 does not exist
evocati@evocati-desktop:~$ 


```

Rather weird given that fstab says it exists.

---

### Post by SeijiSensei on 2017-03-26
/etc/fstab has no idea whether there is a device called /dev/md0.  It just looks for a device with that name.

Apparently your RAID device is not being assembled by mdadm.  Usually if the component devices are marked as "linux_raid_member" they will be assembled automatically at boot.  Did you ever run mdadm initially to define the array?  You need something like
```
sudo mdadm --create /dev/md0 --level=5 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1
```
to create a RAID5 with three components.  It will take a little while to create the array depending on how large the devices are.  You can check on its status with
```
sudo mdadm --detail /dev/md0
```

Once you've done that, you can format the RAID device as ext4 like this:
```
sudo mkfs -t ext4 /dev/md0
```
Now you should be able to mount it into the filesystem tree.

If the components don't assemble properly at boot after doing this, you may need to create the /etc/mdadm.conf file.  See the manual page at "[man mdadm.conf]("https://linux.die.net/man/5/mdadm.conf")" for details.

---

### Post by vrubel68 on 2017-03-26
I assembled this some years ago and it took quite some time to finally get it to work, but I seem to recall mdadm being used.

That being said, I'll have to do the mkfs after I copy the array to the backup drive.

```

evocati@evocati-desktop:~$ sudo mdadm --detail /dev/md0
[sudo] password for evocati: 
mdadm: cannot open /dev/md0: No such file or directory
evocati@evocati-desktop:~$

```

---

### Post by darkod on 2017-03-26
If you have data on the raid that you want to keep, be very careful how you continue because running a wrong command can destroy all the data.

Post the output of this:
```
cat /proc/mdstat
sudo blkid
cat /etc/mdadm/mdadm.conf
```

---

### Post by vrubel68 on 2017-03-26
> **darkod said:**
> If you have data on the raid that you want to keep, be very careful how you continue because running a wrong command can destroy all the data.

Post the output of this:
```
cat /proc/mdstat
sudo blkid
cat /etc/mdadm/mdadm.conf
```


Surething.  I'm in the middle of moving the data off the raid to work on reformatting-copying back.  Besides, with the drives nearing 5 years in operation, I'm starting to get a little concerned they're not backed up.  They're WD Blacks, but still...

Lemme go post that.

```

evocati@evocati-desktop:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : active raid5 sdc1[2] sdb1[1] sdd1[4] sda1[0]
      2930280960 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>
evocati@evocati-desktop:~$

```



```

evocati@evocati-desktop:~$ sudo blkid
[sudo] password for evocati: 
/dev/sda1: UUID="d1aacac0-52dd-4b09-fa52-9eb9bbb22060" UUID_SUB="20718f82-260b-f2d4-6ac6-bed2c6f36f7b" LABEL="evocati-desktop:127" TYPE="linux_raid_member" 
/dev/sdb1: UUID="d1aacac0-52dd-4b09-fa52-9eb9bbb22060" UUID_SUB="29c9c30b-1a17-6f93-0c3a-0c8cd2ba3cf4" LABEL="evocati-desktop:127" TYPE="linux_raid_member" 
/dev/sdc1: UUID="d1aacac0-52dd-4b09-fa52-9eb9bbb22060" UUID_SUB="4a05adc2-c0fa-8eaf-bf81-f38241bf8a5b" LABEL="evocati-desktop:127" TYPE="linux_raid_member" 
/dev/sdd1: UUID="d1aacac0-52dd-4b09-fa52-9eb9bbb22060" UUID_SUB="1b3adfc7-3cc9-9ceb-4f03-32a09e0a08ac" LABEL="evocati-desktop:127" TYPE="linux_raid_member" 
/dev/sde1: UUID="5537ba8b-96f2-4c89-b913-65c06dc8ed96" TYPE="ext4" 
/dev/sde5: UUID="7be7b09c-adfb-4415-b923-67a0a52b44b3" TYPE="swap" 
/dev/sdf1: LABEL="Bulk Files" TYPE="ntfs" 
/dev/md127p1: UUID="279229b0-d042-40f7-b765-998d5f9647cb" TYPE="ext4" 
evocati@evocati-desktop:~$ 

```

```

evocati@evocati-desktop:~$ cat /etc/mdadm/mdadm.conf
ARRAY /dev/md/evocati-desktop:127 metadata=1.2 name=evocati-desktop:127 UUID=d1aacac0:52dd4b09:fa529eb9:bbb22060
MAILADDR root
evocati@evocati-desktop:~$

```

---

### Post by darkod on 2017-03-26
OK. So as you can see, your array is automatically assembled as md127, not md0, md1, etc... The UUID looks correct in blkid, so it all looks good.

The array definition in mdadm.conf is also ok, except that it also uses md127.

There is only one thing I don't like: it seems you have created a partition inside the array because blkid shows /dev/md127p1. mdadm arrays are used directly as a device, like /dev/md127. You usually do not create partition on top of the array. From what we have seen, it seems to be that you need to mount this partition, not the array as you usually would.

I would change one thing in mdadm.conf, I would make the array to be md0:
```
ARRAY /dev/md0 metadata=1.2 name=evocati-desktop:0 UUID=d1aacac0:52dd4b09:fa529eb9:bbb22060
```

Basically in the array definition the metadata info and the name are optional. The only required part is the /dev/mdX and the UUID. mdadm assembles that device from that UUID.

After you make that change, you need to modify fstab accordingly. Assuming the partition on the md0 array will be md0p1, the fstab line would be:
```
/dev/md0p1   /media/raid   ext4   defaults   0   0
```

Of course, comment out or delete from fstab the rest of the lines related to the raid partitions. Then reboot and check if raid assembly and automount work as expected. You can also use the UUID in fstab which is better than /dev/mdX. But note that you need to use the UUID of the filesystem ext4, not the array UUID. You can find all of them in blkid. Like this:
```
UUID=279229b0-d042-40f7-b765-998d5f9647cb   /media/raid   ext4   defaults   0   0
```

That way it should mount the correct partition/array regardless if the /dev/XXX deice name changes.

---

### Post by vrubel68 on 2017-03-26
Ah!  Well, after reading all that, it makes more sense.  I don't recall creating a partition on the raid, but clearly I did.

I looked up changing names on the raid since the UUID shows up in Samba, but all I found for that was changing the md127 to md0 and it wasn't apparent why that was important... Come to think of it, it's still not clear why we need to change the name, but it is clear the UUID and name are used to mount the device and they are in conflict with what fstab is expecting.

Thanks for spending the time to clear things up.

Why is md127 bad to use being as it's what's the raid is assembled to?

Edit:  According to your post a couple years ago, Darkod, using the UUID is probably better in practice than doing the name change to md0.  It begs the question of why bother with the md0 in the first place if it's better to use it, but who wants to type that long a$$ string in everytime they're referring to device [COLOR=#000000][FONT=&quot]279229b0-d042-40f7-b765-998d5f9647cb.[/FONT][/COLOR]  The post in question is here: [https://ubuntuforums.org/showthread.php?t=2265120](https://ubuntuforums.org/showthread.php?t=2265120)

---

### Post by darkod on 2017-03-26
It's not bad to be used, you can keep md127 as long as it's consistent over all other files where it needs to be mentioned.

I simply prefer starting from md0. :)

Besides, since 12.04 ubuntu prefers using uuid in fstab precisely for these situations, so that it does not depend on mdX or sdXY being correct (moving disks around, movinf arrays around, etc). With using the uuid to mount you don't have to worry about md0/127.

---

### Post by vrubel68 on 2017-03-26
It would appear that a great many prefer starting from md0, though if md12x refers to a raid array, I would think it would stick out as such.  Maybe why mdadm was coded to name the arrays as such.

/shrug I know that at one point I had it mounting fine and I could have sworn that it was via UUID, but clearly that broke.

Lemme go out and make these updates to see if they change boot up.

---

### Post by vrubel68 on 2017-03-26
```

ARRAY /dev/md/evocati-desktop:0 metadata=1.2 name=evocati-desktop:127 UUID=d1aacac0:52dd4b09:fa529eb9:bbb22060
MAILADDR root

```




```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc    proc               nodev,noexec,nosuid  0  0  
# / was on /dev/sde1 during installation
UUID=5537ba8b-96f2-4c89-b913-65c06dc8ed96  /        ext4               noauto               0  1  
# swap was on /dev/sde5 during installation
UUID=7be7b09c-adfb-4415-b923-67a0a52b44b3  none         swap               sw                   0  0  

/dev/md0p1                    /media/raid    ext4               defaults             0  0  
;/dev/sdb1                    /media/sdb1    linux_raid_member  defaults             0  0  
;/dev/sdc1                    /media/sdc1    linux_raid_member  defaults             0  0  
;/dev/sdd1                    /media/sdd1    linux_raid_member  defaults             0  0  


```

I used the /dev/md0p1 just to get this going, but the UUID for the ext4 (which I believe you used in you example) is this: /dev/md127p1: UUID="279229b0-d042-40f7-b765-998d5f9647cb" TYPE="ext4"

so I would just drop the UUID in instead of the /dev/md0p1 (clearly from the UUID usage above).

ergo:
```

UUID=279229b0-d042-40f7-b765-998d5f9647cb                  /media/raid    ext4               defaults             0  0  

```


Just confirming myself what you posted on the previous page.  Ended up copy/paste your input and it was identical to what I just did.  Warm and fuzzy feeling. lol

---

### Post by vrubel68 on 2017-03-26
Revised fstab using UUID reference:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc    proc               nodev,noexec,nosuid  0  0  
# / was on /dev/sde1 during installation
UUID=5537ba8b-96f2-4c89-b913-65c06dc8ed96  /        ext4               noauto               0  1  
# swap was on /dev/sde5 during installation
UUID=7be7b09c-adfb-4415-b923-67a0a52b44b3  none         swap               sw                   0  0  

UUID=279229b0-d042-40f7-b765-998d5f9647cb    /media/raid    ext4               defaults             0  0  
;/dev/sdb1                    /media/sdb1    linux_raid_member  defaults             0  0  
;/dev/sdc1                    /media/sdc1    linux_raid_member  defaults             0  0  
;/dev/sdd1                    /media/sdd1    linux_raid_member  defaults             0  0  

```

Alright, after a reboot, it would appear that ; is not comment out.  I think it's usage in the smb.conf through me.  I've revised it thus:


```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc    proc               nodev,noexec,nosuid  0  0  
# / was on /dev/sde1 during installation
UUID=5537ba8b-96f2-4c89-b913-65c06dc8ed96  /        ext4               noauto               0  1  
# swap was on /dev/sde5 during installation
UUID=7be7b09c-adfb-4415-b923-67a0a52b44b3  none         swap               sw                   0  0  

UUID=279229b0-d042-40f7-b765-998d5f9647cb    /media/raid    ext4               defaults             0  0  
#/dev/sdb1                    /media/sdb1    linux_raid_member  defaults             0  0  
#/dev/sdc1                    /media/sdc1    linux_raid_member  defaults             0  0  
#/dev/sdd1                    /media/sdd1    linux_raid_member  defaults             0  0  

```


Additionally, the drive "Bulk Files" didn't automatically mount, but I'm going to play a bit and see if I can't sort that one out on my own given all the information you've already imparted.

---

### Post by vrubel68 on 2017-03-26
Weird:

```

/dev/sdf1: LABEL="Bulk Files" TYPE="ntfs"

```

Bulk Files doesn't appear to have a UUID or is that hidden due to it being an NTFS fms?

Edit:
```

/dev/sdf1                    /media/Bulk\ Files    NTFS            defaults    0    0

```

Because there's a space in the file tree, do I write the fstab as the above or would it just be:

```

/dev/sdf1                    /media/Bulk Files    NTFS            defaults    0    0

```

---

### Post by darkod on 2017-03-26
Actually I never needed to use a path with a space in fstab. I never create mount points with space in them, very bad practice.

As for the label reported by blkid, that's just a label and is not very relevant. The important thing is what you will call the mount point (path), whether /media/BulkFiles or /media/Bulk Files. I recommend the former.

On this topic, why do you plan to use ntfs partition in your linux server?

---

### Post by vrubel68 on 2017-03-26
If I remember correctly, that's drive used to be an OS drive (still has windows installed on it) and I simply plugged it in to the server.  It's large (2tb) and we needed someplace to put back-up files.  I just never got around to reformatting it as it didn't seem to matter when I was shuffling things.

I'd prefer they were all the same, if nothing else than to facilitate installation and management.

---

### Post by vrubel68 on 2017-03-26
It's not liking the /media/BulkFiles mountpoint:

```

Unable to Access "Bulk Files"

Error mounting system-managed device /dev/sdf1: Command-line `mount "/media/BulkFiles"' exited with non-zero exit status 32: mount: unknown filesystem type 'NTFS'

```

This due to the ntfs fs itself?  or is it because I capitalized the fstab specification.

---

### Post by darkod on 2017-03-26
Yes. Google up using ntfs partitions in fstab. I rarely use it and don't know on the top of my head myself. I think the line in fstan should be different, ntfs-3g or something...

PS. Once you have it in fstab you don't have to reboot just to test. For a line that exists in fstab you can test manually with:
```
sudo mount /mountpoint
```

That will pick up the corresponding line from fstab and try to mount the device.

---

### Post by vrubel68 on 2017-03-26
Thank god.  I've been spoiled with my SSD boots so it seems like an eternity rebooting on a platter.

Also it looks like it's either"

> 
Link: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

**File System Type**

[COLOR=#333333][FONT=Ubuntu]You may either use auto or specify a file system. Auto will attempt to automatically detect the file system of the target file system and in general works well. In general auto is used for removable devices and a specific file system or network protocol for network shares.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]Examples:[/FONT][/COLOR]

[LIST]
[*=left]auto
[*=left]vfat - used for FAT partitions.
[*=left]ntfs, ntfs-3g - used for ntfs partitions.
[*=left]ext4, ext3, ext2, jfs, reiserfs, etc.
[*=left]udf,iso9660 - for CD/DVD.
[*=left]swap.
[/LIST]


so this confirms that fstab is also case-sensitive.

---

### Post by vrubel68 on 2017-03-26
Nice.

you threw me with the excplicit /mountpoint in the command line.  took me a second to figure out that that's the drive to be mounted and not the command to use.  Either way it's mounted, so thanks, again.  That was far easier with a bit of coaching.

As a future note (when I'm doing this to a fresh raid), since the mounts changed, I had to update samba/nautilus to re-share them in the new mount points.  No biggie at this point, but it may cause an issue if someone else is reading this in the future.

---

### Post by darkod on 2017-03-26
Yes, linux is ALWAYS case sensitive... Glad you got it sorted.

---

### Post by vrubel68 on 2017-03-26
I certainly appreciate all the help.  I may have been able to sort it all out eventually as Morbius' last comment certainly got me to thinking about connections, but you certainly expedited the whole process by cutting to the chase.

Occam's Razor: the simplest explanation is usually the right one.

---

