---
title: "RAID Level Change - mdadm"
date: 2011-09-30
forum: Server Platforms
---

### Post by dom_madrid on 2011-09-30
Hi,

Using Ubuntu 11.10 server , I am testing RAID level changes through MDADM. The objective is to migrate RAID 1 environment to RAID 5 without data loss.
In order to make as simple as possible, I started in a VM environment (Virtual Box).

**Initial Setup:**
U11.10 + 2 HDD (20GB) in Raid 1 -> no problem
The setup is made with 3 RAID 1 partition on each disk (swap (2GB), boot (500MB), and root (17,5GB)). I understand that this will allow to eventually grow to a RAID 5 configuration and maintain boot on a RAID construct (swap and boot would remain on RAID 1, while root would migrate to RAID 5).

**Increment number of disks:**
add 3 HDD to the setup -> no problem
increase the RAID 1 from 2 HDD to 5 HDD -> no problem, all disks added and synchronized

```

root@ubuntu:~# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md2 : active raid1 sda3[0] sde3[4] sdb3[1] sdc3[2] sdd3[3]
      18528184 blocks super 1.2 [5/5] [UUUUU]

md1 : active raid1 sda2[0] sde2[4] sdb2[1] sdd2[3] sdc2[2]
      488436 blocks super 1.2 [5/5] [UUUUU]

md0 : active raid1 sdb1[1] sde1[4] sda1[0] sdc1[2] sdd1[3]
      1950708 blocks super 1.2 [5/5] [UUUUU]
```[B]
Change Level:[/B]
That's where the problem occurs:
I initially tried 3 different approaches for md2 (the root partition)[INDENT] 1. Normal boot

```
mdadm /dev/md2 --grow --level=5
```Not working: 'Could not set level to raid 5'. I suppose this is because the partition is in use. Makes sense.[/INDENT][INDENT] 2. Boot from the recovery mode in the grub menu
[/INDENT][INDENT] ```
mdadm /dev/md2 --grow --level=5
```Not working: 'Could not set level to raid 5'. Not seing the point of the recovery mode if you cannot make modification...
[/INDENT][INDENT] 3. Boot from the 11.10 CD in rescue mode
I elected not to use a root file system to make the necessary changes, and elected the shell from the installer environment.
No md is currently available
mdadm --assemble --scan
This adds my 3 md, but with a naming convention a bit different than usual:
```
mdadm: /dev/md/2 has been started with 5 drives
mdadm: /dev/md/1 has been started with 5 drives
mdadm: /dev/md/0 has been started with 5 drives
```md/[012] instead of md[012]

```
mdadm /dev/md/2 --grow --level=5
```or
```
mdadm /dev/md2 --grow --level=5
```results in the same message  'Could not set level to raid 5'.

So what am I doing wrong with mdadm ? From the manpage and developper's page, level changes are possible with a simple instruction (with the right version of mdadm of course -hence ubuntu 11.10). But it just does not work.

[/INDENT]I finally tried a fourth and completely different approach:[INDENT]```
mdadm /dev/md2 --stop
mdadm --create --raid-devices=5 --level=5 /dev/md2 /dev/sda3 /dev/sdb3 /dev/sdc3 /dev/sdd3 /dev/sde3
```after the warning about /dev/sd[12345] being part of a raid1 array, it allows to create the raid5 and started it.

```
cat /proc/mdstat
```md2 is being build

```
mdadm -D /dev/md2
```same info

[/INDENT]After waiting for the raid5 to be rebuild, I decided to restart normally the VM... And that's when, I got an unexpected surprise: cannot boot, boot in initramfs. Looks like it cannot find the md with the root in it. 

I googled around but could not find what I missed. I now understand that the fstab (and/or the initramfs image) needed to be updated with the new UUID created but could not figure out how to do it from the CD recovery console (as the fstab points to the one used by the live CD console), and in the case of the busybox showing up with initramfs, I could not locate an editor to try to make changes in it either. 

I am relatively sure I did not destroy the content of the root... just moved it to a different partition that I can no longer access. While trying to mount the new md device, by name does not work (md2 seem to still point to the old raid1). Should I have created the raid device under a different name ? 

Not sure what to update to either as md name keep on changing... md125,md126,md127, or U11:0, U11:1, U11:2. (U11 being the name of the server). Why are raid name changing all the time?

I am convinced I must be missing a simple step, but cannot figure it out so far.
Any help is welcome at this stage.

Dom

---

### Post by dom_madrid on 2011-10-01
At least that part is clear. The last step is no good, but no big loss... its a VM for testing.
How about converting from RAID 1 to RAID 5 then ?

---

### Post by rubylaser on 2011-10-01
> **zackwasa said:**
> Bad news for you. You just destroyed all your previous RAID contents. When you run the --create command with mdadm everything that was there is wiped out. That's why it does not boot for you

This just simply isn't true.  I know it seems like it should destroy the existing data, but the create command doesn't wipe out old data automatically. mdadm will recognize the previous data and try to maintain it.  You'd need to do this from a livecd because your OS is running off this array.  This is just to do the transistion from RAID1 to 5.

```
mdadm --stop /dev/md0
mdadm --stop /dev/md1
mdadm --stop /dev/md2
```

Then create a RAID5 on top of the existing disks. This is the proper way to do this.
```
mdadm --create /dev/md0 --level=5 --raid-devices=2 /dev/sda1 /dev/sdb1
mdadm --create /dev/md1 --level=5 --raid-devices=2 /dev/sda2 /dev/sdb2
mdadm --create /dev/md2 --level=5 --raid-devices=2 /dev/sda3 /dev/sdb3
```

Watch them resync and wait until complete.
```
watch cat /proc/mdstat
```

Once it has finished re-syncing, you can add the other, and “grow” the array to encompass all five disks (obviously, put a partition on each of these new disks).

```
mdadm --add /dev/md0 /dev/sdc1 /dev/sdd1 /dev/sde1
mdadm --add /dev/md1 /dev/sdc2 /dev/sdd2 /dev/sde2
mdadm --add /dev/md2 /dev/sdc2 /dev/sdd2 /dev/sde2
```

Grow the arrays...
```
mdadm --grow /dev/md0 --raid-devices=5
mdadm --grow /dev/md1 --raid-devices=5
mdadm --grow /dev/md2 --raid-devices=5
```

Let them re-sync, then run an fsck on each partition.

You'll need to grow your filesystems to use the new space, and update your /etc/mdadm/mdadm.conf, chroot into the array, and initramfs.  Personally, I would have just built a 3 disk RAID5 array, sync your data over, zero the superblocks on the old disks, and then add them to the new RAID5 array.  That would have been easier, and less error prone. 

This probably doesn't help you now, but maybe it will help someone else in the future.

---

### Post by dom_madrid on 2011-10-06
Hi,

Thanks for the input. I finally got it solved thanks to another entry I made on the Raid Linux Dist List.

My mistake was from trying to convert a 5 HDD RAID1 to a 5HDD RAID5, after having expended the 2HH RAID1 to 5HDD RAID1.

It is actually much easier than that.

Do the RAID5 conversion first, add the new disk, resync the RAID5 and voila. And yes, with mdadm you can create a RAID5 with only 2HDD.

Dom

---

