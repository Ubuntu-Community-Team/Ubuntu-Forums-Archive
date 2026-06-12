---
title: "mdadm array problem. array fails (not degrade) when  one disk is removed from raid5"
date: 2008-11-30
forum: Server Platforms
---

### Post by Underpants on 2008-11-30
I've been toying around all day with the mdadm utility. I have a test machine with a handful of drives running in vmware. I've gotten a good grasp on the commands and what they do. I have created, grown, shrunk, and "software failed" arrays with great success. 

If I shutdown the VM and remove one of the array disks from the machine and then boot the server... I am greeted with the following: 
[IMG]http://absremote.com/aaron/mdadm-01.png[/IMG]

I don't know what all of that means. I can add the disk back, the server will boot and resync and all is well. 

Any idea what's going on here? the filesystem is ext3 and that's what is in my fstab... 

help!

---

### Post by fjgaude on 2008-11-30
I'm not sure but the OS is looking at the mdadm.conf to assemble the array at bootup and it senses that something is wrong, missing, and doesn't know how to handle it.

I've never tried to have drives in VMware Server other than the boot drive where the VMs are.

I suppose if you continued the boot and got into Ubuntu you could assemble the array using the normal command:

```
sudo --assemble --scan
```

or 

```
sudo --assemble /dev/md0
```

If the array assembles you can watch what it is doing using:

```
sudo watch cat /proc/mdstat
```

and then

```
sudo mdadm -D /dev/md0
```

Have you tried any of these?

---

### Post by Underpants on 2008-11-30
```
root@ubuntu:~# mdadm --assemble --scan
mdadm: metadata format 00.90 unknown, ignored.
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.


root@ubuntu:~# mdadm --assemble /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
mdadm: no devices found for /dev/md0

root@ubuntu:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdb[1](S) sdc[2](S)
      4194176 blocks
unused devices: <none>



root@ubuntu:~# mdadm -D /dev/md0
mdadm: metadata format 00.90 unknown, ignored.
mdadm: md device /dev/md0 does not appear to be active.
```



And once I power off the machine, re-add the disk, it boots right up and all is well.
```

root@ubuntu:/home/aaron# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdf[0] sdc[2] sdb[1]
      4194176 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]
unused devices: <none>

```

---

### Post by fjgaude on 2008-11-30
Glad it is working as it should... wish we knew why it is having issues when a drive is removed.

Anyway, good luck computing with raid.

---

### Post by Underpants on 2008-11-30
> **fjgaude said:**
> Glad it is working as it should... wish we knew why is was having issues.

Anyway, good luck computing with raid.



Well, it's NOT working like it should! 


It won't boot properly or rebuild or anything expected if a disk is failed. the original disk has to be re-added for it to work. I'll try this on some test hardware  tomorrow to see if vmware is doing something unexpected.

---

### Post by fjgaude on 2008-11-30
You might have better luck in the Virtualization Forum than here. I don't have a clue... seems if the mdadm.conf file is correct it should assemble with one drive missing... it does if not in VMware. <smile>

I know lots of folks have had issues with external drives, ones not of the virtual OS, even single drives much less arrays.

---

### Post by Underpants on 2008-11-30
Thanks for your help anyway. I have an old whitebox full of 500gb HDD's that I'll put linux on tomorrow at the office and see if my process works... I'm confident that it does but vmware is dinking with it. I'll post back and let you know.

---

### Post by fjgaude on 2008-11-30
I'd appreciate any info you can pass along regarding VMware and arrays. Thanks!

---

### Post by psusi on 2008-12-01
Wow, that error message makes no sense at all.  0.90 is the default metadata format, and it certainly didn't change versions because you unplugged one disk.

What does mdadm -E /dev/sd[abcd] show?

---

### Post by Underpants on 2008-12-02
Built up a hardware box. Followed these steps: 

```
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sdb /dev/sdc /dev/sdd
mkfs.ext3 /dev/md0

*add to fstab
/dev/md0	/mnt/raid	ext3	1 2

mount -a

mdadm --detail --scan --verbose > /etc/mdadm/mdadm.conf


*power off and unplug drive
*power up array does not start

root@ubuntu:/home/aaron# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sdb[1](S) sdc[2](S)
      976772992 blocks

sudo --assemble --scan

*array comes online with 2 out of 3 drives.
```

Is it to be expected that the array does not start automatically? I can see how that would be a safety benefit, but I just want to make sure everything is acting properly.

---

### Post by psusi on 2008-12-03
Yes, arrays will not activate automatically in a degraded state.

---

### Post by Underpants on 2008-12-03
> **psusi said:**
> Yes, arrays will not activate automatically in a degraded state.

Great news! 

Now my next test is to move the array drives into a different computer and see if they will activate!

---

### Post by fjgaude on 2008-12-04
> **Underpants said:**
> Great news! 

Now my next test is to move the array drives into a different computer and see if they will activate!

I've done that many times over the years without issue. The array was always a fully functional one.

The new OS or motherboard was installed along with the array plugged in. Then install mdadm and run the assemble command like so:

```
sudo mdadm --assemble --scan
```

And that does it... new mdadm.conf file created, and the array is ready to mount.

---

### Post by Underpants on 2008-12-17
Still testing things out. When I move the disks to a new system the command "sudo mdadm --assemble --scan" 

just  tells me to piss off and that it cant find anything from a scan or from a config file.

However if I copy my mdadm.conf file from the working system to the new one and reboot, the array picks up just fine. 

Is there a secret to getting --assemble --scan to work?

---

### Post by fjgaude on 2008-12-18
Look, I've never seen it not work. The .conf file is auto created!

Where is your mdadm.conf file? It is normally in /etc/mdadm folder. Has been for about two years.

What does your mdadm.conf file look like, the one that works? And did you see a new one when you moved the array to a new system, installed mdadm, and then ran the --scan?

---

### Post by Underpants on 2008-12-18
my file is at /etc/mdadm/mdadm.conf

```
ARRAY /dev/md0 level=raid5 num-devices=4 metadata=00.90 spares=1 UUID=97b863c1:d58339fc:f289e8f4$
   devices=/dev/sdb,/dev/sdc,/dev/sdd,/dev/sda

```

I have some other lines in there for email and things but those aren't important in regard to this....

I can rename that conf file and reboot the system if there's anything you'd like me to try.

---

### Post by fjgaude on 2008-12-18
A mdadm auto-created mdamd.conf file doesn't have the drive names in it. So you added them by other means?

The way it has always worked for me and others is to do exactly as I suggested: rename or delete the existing mdadm.conf file, remove mdadm from the system, re-boot. Then boot up, add mdadm then run the --assemble --scan command. That auto created .conf file is the one that works.

If you can boot and have an array working using the old .conf file that's fine too.

---

### Post by Chris on 2008-12-18
"--assemble --scan" only works if the devices in the array have the RAID information in the superblock.

How did you create the array?  If you used "build" then they don't have the information in the superblocks.  If you used "create" then they should.

---

### Post by Underpants on 2008-12-18
```
mdadm --create --verbose /dev/md0 --level=5 --raid-devices=3 /dev/sdb /dev/sdc /dev/sdd

```

Thats what I used.

I renamed the conf and rebooted. 
```

aaron@c800:~$ sudo mdadm --assemble --scan
mdadm: No arrays found in config file

```

I recall seeing a command somewhere that can write the superblock?

---

### Post by Chris on 2008-12-18
That create should have added the information to the superblocks.

You know what, I just tried "--assemble --scan" on my own computer and it didn't find any of the arrays either.  They come up fine at bootup though.

---

### Post by fjgaude on 2008-12-18
If you simply renamed the .conf and rebooted that's not going to do it. You have to remove mdadm, reboot and then re-install mdadm, and then --assemble --scan.

---

### Post by Underpants on 2008-12-18
I don't think it will find anything if the array is already active.

Is this the right way to use --examine? Looks like my superblock data is there, doesn't it?

```
aaron@c800:/etc/mdadm$ sudo mdadm --examine /dev/sda
mdadm: metadata format 00.90 unknown, ignored.
/dev/sda:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 97b863c1:d58339fc:f289e8f4:5604163e
  Creation Time : Tue Dec  2 13:07:12 2008
     Raid Level : raid5
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
     Array Size : 1465159488 (1397.29 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Dec 18 10:17:13 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : e91ffe2 - correct
         Events : 32

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8        0        3      active sync   /dev/sda

   0     0       8       16        0      active sync   /dev/sdb
   1     1       8       32        1      active sync   /dev/sdc
   2     2       8       48        2      active sync   /dev/sdd
   3     3       8        0        3      active sync   /dev/sda

```

---

### Post by Chris on 2008-12-18
You may be right about the active arrays.

That "mdadm: metadata format 00.90 unknown, ignored." doesn't look good but I think the rest looks OK.  Maybe the array was created with a newer mdadm than what is currently on the machine?

---

### Post by fjgaude on 2008-12-18
The UUID is the way mdadm knows what to assemble. That UUID should be the same for each drive in the array.

The only thing that is somewhat different than what most folks do is you are using the whole drive and not one partition, sda versus sda1. I've always used the whole drive but as a partition. Can't if that is an issue or not.

Also could you show what this is:

```
sudo mdadm -D /dev/md0
```

That command, the --detail, shows everything. Notice if the UUID is the same for the array as it is for each drive.

The 00.90 is a bug... change it to 0.90 and the error goes away.

---

### Post by Underpants on 2008-12-18
cock

---

### Post by fjgaude on 2008-12-18
The whole process is very complex, believe me. The module called md in the kernel works with mdadm and seems to know if one is there, and if so, has stored data about what is there.

I noticed that your -E on sda shows four drives in raid5. Didn't you say you had three drives in the array?

---

### Post by Chris on 2008-12-18
> **fjgaude said:**
> The 00.90 is a bug... change it to 0.90 and the error goes away.

They must have fixed that in 8.10 because I don't see the error message and I did everything using mostly defaults.

```
mdadm --version
mdadm - v2.6.7 - 6th June 2008
mdadm 2.6.7-3ubuntu8
```

---

### Post by Underpants on 2008-12-18
I expanded the array at one point after my original post just to see how it worked. There are 4 drives now. 

The following steps worked.

```

apt-get remove mdadm
rm /etc/mdadm/mdadm.conf
shutdown -r now
apt-get install mdadm
mdadm --assemble --scan

```

I did create the array from raw drives and not partitions, btw. 

The UUID of md0 and sda are the same

```
/dev/md0  97b863c1:d58339fc:f289e8f4:5604163e
/dev/sda  97b863c1:d58339fc:f289e8f4:5604163e
```

---

### Post by fjgaude on 2008-12-18
There's been many changes to **mdadm** over the last few years... I think the error shows if you created the array with something like 2.6.3 and then use 2.6.7 to test, something like that. Really doesn't do any harm either way through, from what I've read.

---

### Post by fjgaude on 2008-12-18
So, Underpants, compare the new mdadm.conf file with earlier ones... and see what may have been an issue.

One of these days mdadm is going to be as easy to use as hardware raid is, but I think it wil be a few years from now.

Glad you are at or near the bottom of you concerns.

---

### Post by Underpants on 2008-12-18
I see the metadata error thing, EVERYWHERE. I ignore it :) 

This has been a pretty productive thread. Hopefully someone will make good use of it in the future. I should probably edit it down and make a nice blog about the info in it.

I couldn't really find any websites that explain this deeply how to use mdadm. Lots of places say "here's how to make and mount your array!" That's great and all... but being in the technology industry, I'm in a place where I have to test this stuff to death before it can ever leave my office.

Thanks for your help!!!!!!!

---

### Post by fjgaude on 2008-12-18
Wonderful! One of these days a book will come out detailing all the procedures for handling what comes up with **mdadm**, what to do and what not to do. It will be a long book, when you notice how many options and parameters there are in the **man** pages.

Always a joy to help, when I can.

---

### Post by dpeters on 2009-01-10
I have built the software raid array on both server versions 8.04 and 8.10
per the procedures at help.ubuntu.com/8.nn/serverguide. There are some manual things you have to do on both versions in order for booting to work in the degraded condition (one drive out). In version 8.04 grep is not automatically installed on the secondary drive and in 8.10 mdadm must be reconfigured. The procedures are different for each version. As I understand it, if you don't do this and you're testing your array and just happened to unplug the primary drive (where all the boot stuff is) it won't boot (8.04). For 8.10 the change to mdadm affects a line in the mdadm configuration file: "boot_degraded true". It messes up in either version, just for different reasons.

---

### Post by fjgaude on 2009-01-10
> **dpeters said:**
> I have built the software raid array on both server versions 8.04 and 8.10
per the procedures at help.ubuntu.com/8.nn/serverguide. There are some manual things you have to do on both versions in order for booting to work in the degraded condition (one drive out). In version 8.04 grep is not automatically installed on the secondary drive and in 8.10 mdadm must be reconfigured. The procedures are different for each version. As I understand it, if you don't do this and you're testing your array and just happened to unplug the primary drive (where all the boot stuff is) it won't boot (8.04). For 8.10 the change to mdadm affects a line in the mdadm configuration file: "boot_degraded true". It messes up in either version, just for different reasons.

The link you provided doesn't work, likely a typo.

Are you talking about a raid1 array?

What **mdadm** configuration file are you talking about, "boot_degraded true"?

Soon I'll have the hardware to play around with booting from a raid1, two drive array. Will try to write a HOW-TO for what I learn.

---

### Post by Ocelaris on 2010-08-12
> **Underpants said:**
> I see the metadata error thing, EVERYWHERE. I ignore it :) 

This has been a pretty productive thread. Hopefully someone will make good use of it in the future. I should probably edit it down and make a nice blog about the info in it.

I couldn't really find any websites that explain this deeply how to use mdadm. Lots of places say "here's how to make and mount your array!" That's great and all... but being in the technology industry, I'm in a place where I have to test this stuff to death before it can ever leave my office.

Thanks for your help!!!!!!!

This thread absolutely helped me, and it's over a year from when it started. Mdadm rocks, always is reliable, drive fails, sends me an email, and just works... except this time, in 9.04 it didn't activate the array when I booted up, but just mdadm --assemble --scan and it brought the array up, and mdadm -a /dev/md3 /dev/sdb1 and we're back in action :)

This is my favorite how to, I always refer to it (and usually tip the guy in the process)

[http://www.gagme.com/greg/linux/raid-lvm.php](http://www.gagme.com/greg/linux/raid-lvm.php)

---

