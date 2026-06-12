---
title: "resized root partition on RAID 1 setup, now wont boot, stops at initramfs"
date: 2011-05-02
forum: Server Platforms
---

### Post by Foeburner on 2011-05-02
I'm running 10.10 64bit on a RAID1 setup. 

Last week, I resized my root partition using gparted because it was running out of its 9GB space. I successfully resized it over the weekend and now that I'm trying to restart my box, it wont boot up. It goes through the terminal messages (i dont get the ubuntu screen anymore, lost it few versions ago) it stops at INITRAMFS.

I did my research and all the issues regarding this involves something with the USB controller. Didnt work for me tho. 

Let me explain how I resized the partition. I have two 250GB harddrives mirrored to each other and this was my first time using gparted. 

The root partition was 9GB and /var was 230GB. I shrinked down the /var partition on both drives (using the drop down window), i deleted my swap to move the unpartitioned space over and added that space to the root then recreated the swap using ext3 and setting it as primary. I did the same to both drives so they are 100% identical down to the byte!

I assume that RAIDing is at the BIOS level and as long as my partitions are identical, RAID would still work.... right?

It took a whole day for gparted to successfully resize everything. 

This morning I restart and get the error and stops there. I inserted the LIVE CD and i'm able to browse the partitions. Everything is in there and I can see both raided drives... wait... why am I able to see both drives that are raided at the BIOS level and should be recognized by the OS as one?

Did I just lose my RAID setup and thats the reason it wont boot?

how can I reinstall ubuntu without losing not only my data but my configs and all? i have samba, proftpd, openvpn, and all sorts setup and I dont want to lose everything. 

any help is greatly appreciated! :D

---

### Post by Foeburner on 2011-05-02
So when I reboot and I get to the cmd prompt INITRAMFS, the errors that pop before it says:

```

Gave up waiting for root device

Common problems:
-Boot Args (cat /proc/cmdline)
   -Check Root Delay= (Did the system wait long enough?)
   -Check Root= (Did the system wait for the right device?)
-Missing Modules (cat /proc/modules; ls /dev

ALERT!! /dev/md0 does not exist. Dropping to Shell.

```

When I ran
```
cat /proc/cmdline
```

I got:
```
Root=/dev/md0 ro splash vga=792
```

Does this mean root is pointing to the wrong partition? 

2 weeks ago i was recovering a windows hard drive and I mounted in fstab as md0. will this be the cause of the issue?

---

### Post by Foeburner on 2011-05-02
Im having a real hard time researching this. 

I read somewhere that because I resized my raided partitions, that I need to go back and set the raid to the cylinder start/stop?

not sure how to do that but it seems like I have to boot to grub and repair my raid configuration...

---

### Post by Foeburner on 2011-05-02
I rebooted with a liveCD and opened gparted. Gparted recognizes both drives as a RAID. Could I run some kind of raid utility while in the liveCD and repair this or would I have to boot to grub?

anyone?

---

### Post by dtfinch on 2011-05-02
"md" would be Linux software raid, unrelated to the bios.

The output of "fdisk -l" would be helpful. Since it was waiting on md0, I'm guessing / is md0, /var is md1, and swap is either md2 or raw partitions.

MD raid superblocks (with 0.90 metadata, the default) are stored at the end of the partitions. So it would fail to mount / because the superblock is now way before the end, and it would fail to mount /var because the superblock no longer exists.

If you have a third disk lying around, you might want to make a copy of one of the disks as a backup before proceeding, and test whether you can mount each of the partitions on the backup (like sdc1, sdc2, ... rather than md0, md1, if the backup drive is sdc). Since it's raid 1, you should be able to mount them normally if the superblocks are at the end (the default) rather than the beginning. 

I've never had to recreate superblocks in the past, so I'm guessing a little here. I think you would just recreate each raid using mdadm. If gparted resized the filesystems on the individual sd* partitions, rather than on the md* devices, you'd have to let it resync in case it resized them differently at all, otherwise you could use --assume-clean to avoid a resync. But it's probably better to let it resync if there's any chance of filesystem differences.

There's also the matter of the uuids in /etc/mdadm/mdadm.conf, which is also mirrored in the initramfs. The recreated raids might fail to assemble on next boot if they don't match mdadm.conf, and updating initramfs doesn't seem easy on a system that not booting. If you can read mdadm.conf from your backup copy, you'll want to specify the correct uuid for each with --uuid in your mdadm create options.

[man page for mdadm](http://manpages.ubuntu.com/manpages/maverick/man8/mdadm.8.html)

---

### Post by Foeburner on 2011-05-03
dtfinch thanks for the reply!  fdisk -l doesnt produce an output while in the initramfs or using the liveCD. 

I did make a backup of the data as well. 

I read [here]("http://ubuntuforums.org/showthread.php?t=1736742") that the user used this cmd to recreate the array with the correct layout. 
```
 mdadm --create /dev/md0 --assume-clean --level=5 --raid-devices=5 --metadata=0.9 /dev/sdb1 /dev/sdc1 /dev/sde1 /dev/sdd1 missing
```

could I tailor it to this to fit my needs? Is this even feasible for me?
```
mdadm --create /dev/md0 --assume-clean --level=1 --raid-devices=2 --metadata=0.9 /dev/sda1 /dev/sdb1 missing

```

---

### Post by dtfinch on 2011-05-03
> fdisk -l doesnt produce an output while in the initramfs or using the liveCD.
Try "sudo fdisk -l" from the live cd. fdisk prints no output if it's not running as root.

> mdadm --create /dev/md0 --assume-clean --level=1 --raid-devices=2 --metadata=0.9 /dev/sda1 /dev/sdb1 missing

I'd leave off the "missing", and verify that the disks are in fact sda and sdb (drive lettering can change from boot to boot, especially if booting from cd or usb). And I think the "--assume-clean" is only safe if you're certain the partitions are identical. If you leave off "--assume-clean", I think it would copy one partition over the other to ensure they match.

And there may be the problem of the uuids not matching those listed in mdadm.conf. You might need to figure out the ids and specify them with the --uuid option as mentioned before.

Something that worries me a little is that I don't know how you resized the filesystems. If you resized them on the md* devices, I can't picture how you did it using gparted, though I haven't used it in a while. If you resized them individually on the the sd* devices, it would present a couple problems. First, the drives might no longer be identical, which with "--assume-clean" could lead to future corruption, and second, there might not be room left at the ends of the partitions for the md superblocks, so recreating those superblocks could potentially overwrite anything stored at the end of the disk, though you might not notice until you try to access the affected file(s).

---

