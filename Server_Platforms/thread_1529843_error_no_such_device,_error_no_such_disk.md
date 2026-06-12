---
title: "error: no such device, error: no such disk"
date: 2010-07-12
forum: Server Platforms
---

### Post by X1R1 on 2010-07-12
I am getting the same errors everytime I boot the server up:

Error: no such device {SOME-UUID}
Error: no suck disk

After that the system boots normally, but Im afraid ignoring this error can make my system crash in the future.

I figured it was a grub error and I tried the update-grub2 command, it does detect all installed kernels no problem, but after I reboot I get the same error message.

What can I do?

Regards and thanks in advance for the help

---

### Post by ruffEdgz on 2010-07-13
I'm curious what is in your /etc/fstab file. Can you post that configuration on this post and if you can get the last four digets of the {SOME-UUID} error message, that might also help with why its coming up.

Thanks!

---

### Post by X1R1 on 2010-07-13
ruff, thanks for your reply, here is the info:

> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md0 during installation
UUID=5d6077d9-36a0-4662-8fd1-4fd5f0072cb8 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=f3a9af09-b7b5-4063-bffc-f02d02f2fa68 /boot           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=53361338-2988-40f8-a633-cb48da99875a none            swap    sw              0       0

Also I forgot to mention, this server setup is running on RAID1 with two 1TB hard drives. Also, since I read that placing the /boot partition on a raid array might cause problems, this server has another 250 gb  hard drive in which the /boot partition resides. So to sumarize:

/boot = 250GB hard drive
/ = 1TB RAID1 array

About the last digits of the UUID, I will need to manually restart the server and cant do it at this time cause it is a file server and everyone is using it at the moment. But tomorrow night I will surely have the output.

thanks in advance

---

### Post by ruffEdgz on 2010-07-13
Thanks for the reply. Any information about that UUID error would be helpful so when you get a chance.

When looking at your fstab, it seems it might be the swap since you are able to restart your server without any problems outside from that error coming up. If you do a:
```
cat /proc/swaps
```
or
```
free -m | grep -i swap
```
does that come up as being used or mounted?

Also, can you do a
```
mount | grep boot
```
to see if your /boot partition is also mounted. I don't see why it wouldn't but I highly doubt its your slash (/) parition that is coming up with this error (but it might be because of the RAID1 setup).

Another question: Can I assume you are using a hardware RAID for / ??

Thanks!

---

### Post by X1R1 on 2010-07-13
ruff, here is the output of the commands, and no, im not using hardware RAID, Im using software RAID with mdadm, just checked the array and all is in order :D

> aaaa@ML115:~$ cat /proc/swaps
Filename				Type		Size	Used	Priority
/dev/sda5                               partition	7811064	0	-1

aaaa@ML115:~$ free -m | grep -i swap
Swap:         7627          0       7627

aaaaa@ML115:~$ mount | grep boot
/dev/sda1 on /boot type ext3 (rw)

thanks for the help

---

### Post by ruffEdgz on 2010-07-13
Great, so no we know it isn't swap or /boot, I will wait until you can restart it and try and get some information about the error UUID. Once you get that and the server is started up, can you do the following command:
```
blkid /dev/sd*
```
Paste the result of that on this post as well with what you can find from that error UUID you can find.

Thanks!

---

### Post by X1R1 on 2010-07-19
Im back! sorry about the long delay but I didnt have time to di it.

After lots of restarts (lol) here is the complete UUID displayed at booting:

> 
Error: no such device 5D6077D9-36A0-4662-8FD1-4FD5F0072CB8
Error: no such disk

And here is the output of sudo blkid /dev/sd*

> 
aaaa@ML115:~$ sudo blkid /dev/sd*

/dev/sda1: UUID="f3a9af09-b7b5-4063-bffc-f02d02f2fa68" TYPE="ext3"
/dev/sda5: UUID="53361338-2988-40f8-a633-cb48da99875a" TYPE="swap"
/dev/sdb1: UUID="a7c3b861-f3cf-b50b-0e61-9c2a6e9739d4" TYPE="linux_raid_member"
/dev/sdc1: UUID="a7c3b861-f3cf-b50b-0e61-9c2a6e9739d4" TYPE="linux_raid_member"


Well, as you can see the UUID displayed at the start isnt on that list, but I figured that the command you said me to type was to see only sdX drives, and since I have a RAID1 array, it is named mdX so if figured I could just:

> aaaa@ML115:~$ sudo blkid /dev/md*
/dev/md0: LABEL="RAID1A" UUID="5d6077d9-36a0-4662-8fd1-4fd5f0072cb8" TYPE="ext4"

So, THAT ONE is the conflicting UUID, apparently, Ubuntu cant find the array at boot, but after it boots everything is normal. I have checked the array with the following command:

> aaaa@ML115:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Tue May 18 16:45:06 2010
     Raid Level : raid1
     Array Size : 976760768 (931.51 GiB 1000.20 GB)
  Used Dev Size : 976760768 (931.51 GiB 1000.20 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Jul 19 15:35:33 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : a7c3b861:f3cfb50b:0e619c2a:6e9739d4
         Events : 0.267582

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1


All appears normal, but the UUID there is different from what "sudo blkid /dev/md*" shows, and its exactly the same as the /dev/sdc1 and /dev/sdb1. Im confused but I think we have arrived at the root of the problem.

Hope you guys can help me out :D

regards

---

### Post by ruffEdgz on 2010-07-19
Glad to see that you were able to grab that UUID that was having the error.

It makes sense now but I'm curious if you are in read-only mode for your server (/) or if you are in read-write mode (do the command "mount" to see if your root (/) parition is in rw or ro)?

Also, can you show us the results of the following commands:
```

ls -l /dev/disk/by-uuid/
ls -l /dev/disk/by-id/

```

Just from looking at your fstab and your mdadm command results, it looks like there shouldn't be any issues. I will see what things I can do to try and similate this behavior. Thanks for narrowing this down some and its getting closer to knowing why it might be trying this error.

FYI - I forgot we probably could have gotten that UUID without rebooting by looking at the logs in /var/logs/ so I'm sorry that you had to restart it a few times. It won't happen again.

---

### Post by X1R1 on 2010-07-19
mount command gives me this:

> /dev/md0 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda1 on /boot type ext3 (rw)

Then:
> 
aaaa@ML115:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2010-07-19 15:21 53361338-2988-40f8-a633-cb48da99875a -> ../../sda5
lrwxrwxrwx 1 root root  9 2010-07-19 15:21 5d6077d9-36a0-4662-8fd1-4fd5f0072cb8 -> ../../md0
lrwxrwxrwx 1 root root 10 2010-07-19 15:21 f3a9af09-b7b5-4063-bffc-f02d02f2fa68 -> ../../sda1

And finally (this one is a little long):

> aaaa@ML115:~$ ls -l /dev/disk/by-id/
total 0
lrwxrwxrwx 1 root root  9 2010-07-19 15:21 ata-GB0250EAFJF_9SF1LNFQ -> ../../sda
lrwxrwxrwx 1 root root 10 2010-07-19 15:21 ata-GB0250EAFJF_9SF1LNFQ-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-07-19 15:21 ata-GB0250EAFJF_9SF1LNFQ-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-07-19 15:21 ata-GB0250EAFJF_9SF1LNFQ-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 2010-07-19 15:21 ata-ST31000528AS_5VP47W24 -> ../../sdc
lrwxrwxrwx 1 root root 10 2010-07-19 15:21 ata-ST31000528AS_5VP47W24-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 2010-07-19 15:21 ata-ST31000528AS_9VP5G66V -> ../../sdb
lrwxrwxrwx 1 root root 10 2010-07-19 15:21 ata-ST31000528AS_9VP5G66V-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 2010-07-19 15:21 md-uuid-a7c3b861:f3cfb50b:0e619c2a:6e9739d4 -> ../../md0
lrwxrwxrwx 1 root root  9 2010-07-19 15:21 scsi-SATA_GB0250EAFJF_9SF1LNFQ -> ../../sda
lrwxrwxrwx 1 root root 10 2010-07-19 15:21 scsi-SATA_GB0250EAFJF_9SF1LNFQ-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-07-19 15:21 scsi-SATA_GB0250EAFJF_9SF1LNFQ-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-07-19 15:21 scsi-SATA_GB0250EAFJF_9SF1LNFQ-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 2010-07-19 15:21 scsi-SATA_ST31000528AS_5VP47W24 -> ../../sdc
lrwxrwxrwx 1 root root 10 2010-07-19 15:21 scsi-SATA_ST31000528AS_5VP47W24-part1 -> ../../sdc1
lrwxrwxrwx 1 root root  9 2010-07-19 15:21 scsi-SATA_ST31000528AS_9VP5G66V -> ../../sdb
lrwxrwxrwx 1 root root 10 2010-07-19 15:21 scsi-SATA_ST31000528AS_9VP5G66V-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 2010-07-19 15:21 wwn-0x5000c5001a7f05f2 -> ../../sda
lrwxrwxrwx 1 root root 10 2010-07-19 15:21 wwn-0x5000c5001a7f05f2-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-07-19 15:21 wwn-0x5000c5001a7f05f2-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-07-19 15:21 wwn-0x5000c5001a7f05f2-part5 -> ../../sda5
lrwxrwxrwx 1 root root  9 2010-07-19 15:21 wwn-0x5000c5001ff3ab32 -> ../../sdb
lrwxrwxrwx 1 root root 10 2010-07-19 15:21 wwn-0x5000c5001ff3ab32-part1 -> ../../sdb1
lrwxrwxrwx 1 root root  9 2010-07-19 15:21 wwn-0x5000c500219690a1 -> ../../sdc
lrwxrwxrwx 1 root root 10 2010-07-19 15:21 wwn-0x5000c500219690a1-part1 -> ../../sdc1


---

### Post by X1R1 on 2010-07-19
> **ruffEdgz said:**
> 
FYI - I forgot we probably could have gotten that UUID without rebooting by looking at the logs in /var/logs/ so I'm sorry that you had to restart it a few times. It won't happen again.

Its ok its for the best :D better to see it with my own eyes than on a log :popcorn:

---

### Post by ruffEdgz on 2010-07-26
Ok, so I did a test and could not come up with the same issue that you see on your server (when I made my software RAID test, I made sure I had a simliar setup what was place above). Some other ideas that you could try would be to:

 * Edit /ect/fstab
 * copy and paste this line on the same file: ```
UUID=5d6077d9-36a0-4662-8fd1-4fd5f0072cb8 / ext4 errors=remount-ro 0 1
```
 * comment out one of the copied lines
 * edit the uncommented line so it says:
```
/dev/md0 / ext4 errors=remount-ro 0 1
```
 * restart your server to see if the error still comes around

I did this on the test server and it booted up just fine. Because this involves a restart, you might want to plan on doing it when you can. 

Also, because I can't get this error on my own box, I would plan a 'disaster recovery plan' if this change doesn't work. The disaster recovery would be to make sure you can get into your system through single or emergency mode OR have a LiveCD you can boot into, mount to your drive and make the changes to your systems /etc/fstab so it points to the UUID. I am 99.5% that it will work but since I can't reproduce that same error, who knows if this suggestion will help or hurt it. I just want to forewarn you before you make any changes to your prod system.

From the small diagnosis that was taken on this post, it doesn't look like the error you are receiving is accurate. If it couldn't find that device on your system, the system would just halt there and wait for a reboot. The reason is the error is saying that root (/) can't be found and you are able to login and show that the mount of root is ok.

Sorry for the late reply on this but just really busy at work.

---

### Post by X1R1 on 2010-07-27
Ruff,

Thanks a lot for all the help so far, I will try this and come back with results. I have a question though, when you say:

*comment out one of the copied lines
*edit the uncommented line so it says

...

What do you mean by that? I mean, i should add the info in the second command to the md0 entry on fstab? And what do I have to comment out?

Also according to the fstab I posted earlier on this thread the entry you propose first (the UUID one) its already there.

So, from what I understand its just adding the md0 entry in my fstab? I will await for your response before doing this. 

Cheers

---

### Post by ruffEdgz on 2010-07-27
Sorry about that. Below is an example of what you should see with the suggested idea when editing your /etc/fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/md0 during installation
#UUID=5d6077d9-36a0-4662-8fd1-4fd5f0072cb8 / ext4 errors=remount-ro 0 1
/dev/md0 / ext4 errors=remount-ro 0 1
# /boot was on /dev/sda1 during installation
UUID=f3a9af09-b7b5-4063-bffc-f02d02f2fa68 /boot ext3 defaults 0 2
# swap was on /dev/sda5 during installation
UUID=53361338-2988-40f8-a633-cb48da99875a none swap sw 0 0

```
I was just making sure you kept the original line of text (its commented out) but placed in the suggested line as the one to use. Its easier to change if anything happens.

Glad to help and best of luck.

::NOTE::
I was looking around the ubunut 10.04 known issues section and found this part that could be the same for software RAIDs as well -- [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#LVM%20filesystems%20should%20be%20listed%20in%20/etc/fstab%20by%20name](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#LVM%20filesystems%20should%20be%20listed%20in%20/etc/fstab%20by%20name)

Just an idea but like I said, I wasn't able to reproduce that error on my software RAID to make it so.

---

### Post by X1R1 on 2010-07-28
Just to have the information organized and people get a better idea of what we are talking about I will post the text here:

> LVM filesystems should be listed in /etc/fstab by name

In general, filesystems are listed in /etc/fstab by UUID rather than by device name, to ensure that the filesystem can always be found reliably. If you are mounting a filesystem located on LVM, however, it is recommended that you list them in /etc/fstab by device name, not by UUID, because UUIDs are not unique if LVM snapshots are used, which can result in wrong filesystems being mounted at boot. (563902) 

According to that, UUID are NOT unique if you use LVM, but the same thing applies for software RAID, just take a look at the earlier posts about UUID and you will find the raid array members have the same UUID.

This could possibly be the cause of the error.

---

### Post by X1R1 on 2010-08-20
Hi again, Im back with the results from changing fstab.

no luck, exact same error appears, UUID line is commented out and /dev/md0 put in place but still same behaviour.

Dunno what to do anymore this is really strange.

I know its been a long time since I posted but was way to busy to try the solution until now.

---

### Post by Der_King on 2012-06-26
Hi,

Probably module lvm was not loaded into gub, grub was not able to locate the designate root filesystem.

Please check if the following line is available within grub configuration (/boot/grub/grub.cfg):
[INDENT]...
  insmod video_cirrus
}

**insmod lvm**
insmod part_msdos
insmod ext2
set root=...
[/INDENT]
After modifying, no grub configuration is needed ("grub-install ..."), just a reboot is required.

Greetz!

---

