---
title: "LUKS data loss on RAID1 HELP!"
date: 2008-05-30
forum: Security
---

### Post by thehighhat on 2008-05-30
Need help recovering data from my hard drives.

Two disks, each with several partitions like:

/dev/sda1
/dev/sda2
/dev/sda3

/dev/sdb1
/dev/sdb2
/dev/sdb3

/dev/sda1 & /dev/sdb1 are RAID1 /dev/md0, with ext3, /boot
/dev/sda2 & /dev/sdb2 are RAID1 /dev/md1, with ext3, /
/dev/sda3 & /dev/sdb3 are RAID1 /dev/md2, with luksFormat aes-cbc-essiv:sha 256 encrypted data, which then has ext3, /home

--- so what is wrong

sda died and is not recognized by motherboard

During boot up, I am asked for LUKS passphrase as normal, but it does not unlock the drive.  Justs gives an error message and asks again.

I can boot with /home mounted.  

I see /dev/md0 (/boot) and /dev/md1 (/) are present.

BUT there is NO /dev/md2 (/home).

What happened to it!!!!

It should still show up even if it cannot be unlocked.

So even trying to luksOpen partition 3 or /dev/md2 manually fails.

PLEASE ADVISE.

---

### Post by thehighhat on 2008-05-30
More info:

/proc/mdstat says that /dev/md2 is inactive.  (unexpected)

/dev/md0 and /dev/md1 are degraded (this is expected)

---

### Post by hyper_ch on 2008-05-31
dunno about raid BUT if the drive would be normally accessible you can access it like this:
```

sudo cryptsetup luksOpen /dev/DEVICE MAPPERNAME
sudo mount /dev/mapper/DEVICE /media/MAPPERNAME

```

If that does not work, you may have to load the crypto modules first:
```

sudo modprobe aes
sudo modprobe dm-crypt
sudo modprobe dm_mod

```

---

### Post by dakal on 2008-05-31
Since RAID 1 is mirroring, you should be able to bypass the RAID completely and point LUKS at the remaining /dev/sd?3. If the hard disk is not recognized by the motherboard during the BIOS POST it is always possible that the electronics are shot, in which case Linux won't be able to use it either and the drive that was previously /dev/sdb now shows up as /dev/sda. dmesg (or the kernel log) will let you see the kernel device and partition scan which should give some more clues there.

---

### Post by thehighhat on 2008-06-02
> **hyper_ch said:**
> dunno about raid BUT if the drive would be normally accessible you can access it like this:
```

sudo cryptsetup luksOpen /dev/DEVICE MAPPERNAME
sudo mount /dev/mapper/DEVICE /media/MAPPERNAME

```

If that does not work, you may have to load the crypto modules first:
```

sudo modprobe aes
sudo modprobe dm-crypt
sudo modprobe dm_mod

```



No go.

The correct modules are loaded.

I can mount other crypto partitions on this disk w/o any problem.

There is nothing unusual in dmesg so I don't know why the raid1 functioning disk is not working.  Or more precisely, I don't know why two of four raid1 appear inactive (/home and /data) and two of them are useable (/boot and /).  

Raid is not a backup.  

I have learned this lesson the hard way.

---

### Post by thehighhat on 2008-06-02
> **dakal said:**
> Since RAID 1 is mirroring, you should be able to bypass the RAID completely and point LUKS at the remaining /dev/sd?3. If the hard disk is not recognized by the motherboard during the BIOS POST it is always possible that the electronics are shot, in which case Linux won't be able to use it either and the drive that was previously /dev/sdb now shows up as /dev/sda. dmesg (or the kernel log) will let you see the kernel device and partition scan which should give some more clues there.

Yes, the drive is dead.  Nothing I can do about that.

The partition table is correct.  /proc/mdstat even has all of the raid devices listed (4 of them).  But some of them appear inactive.  And those are the partitions that have valuable data.

Since the /dev/md? is inactive, AND I cannot cryptsetup luksOpen the partition /dev/sd? directly for some strange reason, I am screwed.

---

### Post by thehighhat on 2008-06-02
FYI, I did find a backup so things are looking better.

This was my setup:

OS, swap, etc... on disk
data to day work and critical data in raid1 mirror.
those mirrors backed up manually once a month to another disk.

So I have just over a month of data loss with this setup.

---

### Post by hyper_ch on 2008-06-03
always make backups...

---

### Post by thehighhat on 2008-06-03
SOLVED -  recovering data from my hard drives.

Two disks, each with several partitions like:

/dev/sda1
/dev/sda2
/dev/sda3
/dev/sda4

/dev/sdb1
/dev/sdb2
/dev/sdb3
/dev/sdb4

/dev/sda1 & /dev/sdb1 are RAID1 /dev/md0, with ext3, /boot
/dev/sda2 & /dev/sdb2 are RAID1 /dev/md1, with ext3, /
/dev/sda3 & /dev/sdb3 are RAID1 /dev/md2, with luksFormat aes-cbc-essiv:sha 256 encrypted data, which then has ext3, /home
/dev/sda4 & /dev/sdb4 are RAID1 /dev/md3, with ext3, /data


sdb died and is not recognized by motherboard

During boot up, I am asked for LUKS passphrase as normal, but it does not unlock the drive.  Justs gives an error message and asks again.

I see /dev/md0 (/boot) and /dev/md1 (/) are present.

BUT there is NO /dev/md2 (/home) or /dev/md3 (/data)

SOLVED:

-----------------------------------------------

I found a solution to the problem, although I do not quite know why this works. Here are the steps (verbose for the sake of google searches)

1. tried to mount the /dev/sda4 member of the unencrypted inactive /dev/md3 gave error:

unknown filesystem type linux_raid_member

1b. changed filesystem id of /dev/sda4 to linux (83) from raid autodetect (fd)

1c. this step (1b) may have been irrelevant

2. tried to cryptsetup luksOpen failed on the encrypted inactive raid member and the raid device

3. mdadm --stop /dev/md3 to turn off the inactive member; same for /dev/md2

4. then mounting the unencrypted raid member device worked

5. then luksOpen worked for encrypted raid member device as well 

5b. mounted the decrypted /dev/sda3

HAPPY.

---

### Post by paul382 on 2008-10-03
Hi,

To recover your hard drive you should use Stellar Phoenix [Data recovery]("http://www.stellarinfo.com") software. This software helps you to recover files and data from damaged hard drive.

---

