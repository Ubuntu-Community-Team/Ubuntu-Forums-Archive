---
title: "Raid array incorrectly assembled on boot"
date: 2011-02-20
forum: Server Platforms
---

### Post by nashibuntu on 2011-02-20
Hi there.

I've got a couple of new hard disks that I have partitioned (3 partitions per disk) and set up in a mirrored software raid array using mdadm. They've synced, I've put file systems on them (1 x ext4, 2 x luks + ext4) and I can mount them. I've checked the partitions using fdisk. I've checked the filesystems using fsck. So far so good.

Next step is that I'd like mdadm to automatically assemble them on boot. (Not bothered about mounting and crypttabing yet.)

I've used

[FONT="Lucida Console"]sudo /usr/share/mdadm/mkconf[/FONT]

to generate a new mdadm.conf with the appropriate UUIDs for the new partitions. I've checked that this matches the output of

[FONT="Lucida Console"]sudo mdadm --detail --scan[/FONT]

The new lines in this file are:

[FONT="Lucida Console"]ARRAY /dev/md9 level=raid1 num-devices=2 UUID=470fb8a6:45561fe0:ebda4a02:9ba7a1ed
ARRAY /dev/md10 level=raid1 num-devices=2 UUID=f351fbba:c704a4b2:ebda4a02:9ba7a1ed
ARRAY /dev/md8 level=raid1 num-devices=2 UUID=c6ccec17:2274588e:ebda4a02:9ba7a1ed[/FONT]

To check that the mdadm.conf is fine I have stopped the new arrays:

[FONT="Lucida Console"]sudo mdadm --stop /dev/md8
sudo mdadm --stop /dev/md9
sudo mdadm --stop /dev/md10[/FONT]

and then automatically reloaded them from mdadm.conf using

[FONT="Lucida Console"]sudo mdadm --assemble --scan[/FONT]

They get added just fine. The output of cat /proc/mdstat verifies that.

[FONT="Lucida Console"]md8 : active raid1 sda3[0] sdb3[1]
      767046272 blocks [2/2] [UU]

md10 : active raid1 sda2[0] sdb2[1]
      104857536 blocks [2/2] [UU]

md9 : active raid1 sda1[0] sdb1[1]
      104857536 blocks [2/2] [UU][/FONT]

I've also updated my initramfs with

[FONT="Lucida Console"]sudo update-initramfs -u[/FONT]

Now I reboot. The system boots fine. However, when I check /proc/mdstat I find that out of the new arrays, only the standard ext4 formatted one, /dev/md8 has assembled. Furthermore, rather than being marked up as attached to the third partitions of /dev/sda and /dev/sdb as expected, it is marked up as being attached to the whole disks, but with the size of the third partition:

[FONT="Lucida Console"]md8 : active raid1 sdb[1] sda[0]
      767046272 blocks [2/2] [UU][/FONT]

/dev/md9 and /dev/md10, which should be formed from mirrored first and second partitions (luks + ext4 formattted) respectively have not been assembled at all. When I look in dmesg I see a message that says:

[FONT="Lucida Console"]md8: p3 size 1534092720 extends beyond EOD, truncated[/FONT]

It looks like it is expecting partition 3 to be the size of the whole disk. If I stop the incorrect /dev/md8 array it has created at boot using

[FONT="Lucida Console"]mdadm --stop /dev/md8[/FONT]

and then do

[FONT="Lucida Console"]sudo mdadm --assemble --scan[/FONT]

it assembles correctly as you would expect it to:

[FONT="Lucida Console"]mdadm: /dev/md9 has been started with 2 drives.
mdadm: /dev/md10 has been started with 2 drives.
mdadm: /dev/md8 has been started with 2 drives.[/FONT]

Does anyone know why it would fail to assemble correctly on boot, yet assemble just fine when mdadm.conf is loaded once logged in after boot? I have searched around to see if I can find someone else that has had the same problem. The closest problem I have encountered is described here:

[https://bbs.archlinux.org/viewtopic.php?pid=826450]("https://bbs.archlinux.org/viewtopic.php?pid=826450")

The workaround in that case was to add some kernel parameters to tell it how to configure the raid array. It's as if mdadm.conf isn't being read properly or the kernel hasn't been updated correctly by initramfs-update -u. Some how the luks encrypted partitions are confusing it - but only on boot. Could anyone here offer help\advice as to how to get this working correctly?

Thank you.

---

### Post by nashibuntu on 2011-02-21
No takers? I have just been having a read of the [linux raid documentation]("https://raid.wiki.kernel.org/index.php/Linux_Raid"), which I only just found. (I had been focussing on Ubuntu docs before.)

I originally formatted my partitions as standard linux partitions. However, once assembled fsck would output error messages like: "The file system size (according to the superblock) is xxx blocks. The physical size of the device is yyy blocks. Either the superblock or the partition table is likely to be corrupt." So, I figured that maybe I should have been using "linux raid autodetect". When I repartitioned using that format the error message went away - so I guessed that this was necessary when using raid and I continued with it.

Now having read the docs I realise that the autodetection might actually be the source of the problems. A (failed) attempt is probably being made to auto-assemble the arrays on boot without consideration of the contents of mdadm.conf.

I am going to start again. This time I am going to use standard linux partitions. Furthermore, following the recommendation in the docs, I am going to use --metadata=1.2 since none of the partitions are boot partitions.

If I get the same filesystem size mismatch error, then I'll try resizing after the raid is set-up. Wish me luck!!

---

### Post by rubylaser on 2011-02-22
What do you mean by this...
> I originally formatted my partitions as standard linux partitions

Did you set them up with fdisk as Linux raid autodetect partitions?  Like this...
```
Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00096494

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *           1      121601   976760001   fd  Linux raid autodetect
```

---

### Post by rubylaser on 2011-02-22
Using metadata 1.2 is a good idea too.

---

### Post by nashibuntu on 2011-02-22
> **rubylaser said:**
> What do you mean by this...


Did you set them up with fdisk as Linux raid autodetect partitions?  Like this...
```
Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00096494

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1   *           1      121601   976760001   fd  Linux raid autodetect
```

I have made several attempts at partitioning the disks. The first time I used the Linux system type. So something like this:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   195354565    97676259   83  Linux
/dev/sda2       195354566   390707083    97676259   83  Linux
/dev/sda3       390707084  1953525167   781409042   83  Linux
```

I specified the partition sizes in Gigabytes like so: "+100G". I used the default metadata type of 0.9 when creating the raid arrays. However, when I created the file systems I got those error messages telling me about the size mismatch.

On my second attempt I repartitioned using the "Linux raid autodetect" system type as above. I also specified the partition sizes in Gigabytes. I used the default metadata type of 0.9 when setting up the raid arrays. That time I had problems with the raid arrays incorrectly assembling on boot.

I'm now onto my third attempt. I have repartitioned using the standard "Linux" system type. I specified the partition sizes in sectors like so: +97676259. This time I created the raid arrays explicitly specifying metadata=1.2. So far so good. I have created file systems on the partitions and fsck verifies that everything is okay, so I have at least managed to eliminate the problem with the error message about invalid filesystem size. The final test is being able to reboot and have the arrays assemble correctly as per mdadm.conf. I'm feeling hopeful that it will work. I'll test it this evening and report back how it goes.

Thanks for your help.

---

### Post by nashibuntu on 2011-02-22
My third attempt worked. In summary, to ensure that these new (non-boot) encrypted and non-encrypted ext4 raid-mirrored partitions worked correctly (that is assembled correctly on boot and didn't have inconsistently-sized file systems) I did the following (order important):

[LIST=1]
[*]Used fdisk to partition the new disks (using the default "Linux" system type.)
[*]Specified the partition sizes in sectors, not Gigabtes. (I don't think this is important - but I list it here just in case.)
[*]Created the raid arrays using the --metadata=1.2 option.
[*]Created the file systems on the assembled arrays using cryptsetup, and mkfs as normal.
[*]Checked that the new file systems are okay using fsck.
[*]Used the output of /usr/share/mdadm/mkconf to update my /etc/mdadm/mdadm.conf file.
[*]Used the output of ls -l /dev/disk/by-uuid/ to identify the uuids required to update the /etc/fstab file with mount information. (I didn't want my encrypted device-mapped drives to be auto-mounted so I used the noauto option for those.)
[*]Updated my initramfs using update-initramfs -u
[*]Rebooted and confirmed that everything assembled and mounted correctly (using cat /proc/mdstat and mount)
[/LIST]

---

### Post by rubylaser on 2011-02-22
I'm glad you got it working.  I've never used anything other than linux raid autodetect for the partition identifier, so I wonder why it didn't work in your case.

---

### Post by nashibuntu on 2011-02-22
Me neither, but I'd never used it with luks encrypted partitions before. That appears to be the thing that confused it.

---

