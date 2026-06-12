---
title: "RAID fails immediately after installation"
date: 2010-06-15
forum: Server Platforms
---

### Post by Pitt Stains on 2010-06-15
Hello,

I've installed Ubuntu 10.04 LTS (64-bit) server edition on a box here (a few times now), and each time I attempt to boot post-install, I get RAID errors.  The box has 4 hard drives in it, and I've disabled the hardware RAID in BIOS because I couldn't seem to get that to work.

During the installation, I opted to handle partitioning manually.  One set of hard drives has two partitions: one for swap, and one for /.  When all is said and done, I end up with three RAID 1 mirrors: one for swap (/dev/md0), one mounted at / (/dev/md1), and one mounted at /srv (/dev/md1).

After installation is complete, I'm prompted to restart the system, upon which I get the following message:

```
** WARNING: There appears to be one or more degraded RAID devices **

The system may have suffered a hardware fault, such as a disk drive failure.  The root device may depend on the RAID devices being online.  One or more of the following RAID devices are degraded:
Personalities: [linear][multipath][raid0][raid1][raid6][raid5][raid4][raid10]

md0:    inactive dm-1[1](S)
        1961920 blocks

md2:    active raid1 sdb1[1] sda1[0]
        1953513408 blocks [2/2] [UU]
        [=>...................]  resync = 6.3% (123334848/1953513408) finish=585.
9min speed=52053K/sec

unused devices: <none>
Attempting to start the RAID in degraded mode...
mdadm: CREATE user root not found
mdadm: CREATE group disk not found
mdadm: /dev/md0 has been started with 1 drive (out of 2).
mdadm: no devices found for /dev/md1
Started the RAID in degraded mode.
Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/04aa1fe9-7fcb-46bf-80df-1a0a2efc719a does not exist. Dropping to a shell!
```

Here's some more output that may be useful in identifying the problem:

```

(initramfs) cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.32.21-server root=UUID=04aa1fe9-7fcb-46bf-80df-1a0a2efc719a ro quiet

(initramfs) blkid
/dev/sda1: UUID="aa978c97-a943-e9ac-5640-27138e5b6526" TYPE="linux_raid_member"
/dev/sdb1: UUID="aa978c97-a943-e9ac-5640-27138e5b6526" TYPE="linux_raid_member"
/dev/sdc: TYPE="promise_fasttrack_raid_member"
/dev/md2: UUID="c7f12a9c-73b2-40e2-ad66-713d4d5f91a3" TYPE="ext4"
/dev/sdd: TYPE="promise_fasttrack_raid_member"
/dev/mapper/pdc_eccefcaehd1: UUID="0a1aa4d4-ac88-264f-1af5-d787c53c72c0" TYPE="linux_raid_member"
/dev/md0: UID="a2a26e06-6b24-4920-9cc0-6446800f8372" TYPE="swap"

```

I suspect that the hardware RAID controller is interfering with the software RAID, even though the former is turned off in the BIOS.  "Promise" and "Fasttrack" are names associated with the onboard RAID controller; since my RAID arrays are all supposed to be in the software, I'm expecting them all to be of type linux_raid_member.

I'm puzzled that md0 (swap) comes up, but not md1 (/), as md0 and md1 depend on the same two disks.

Anyone seen this before?  Have any suggestions for rectifying this?

---

### Post by uOpt on 2010-06-15
dmesg?

---

### Post by maferrer on 2010-06-18
If not exists /dev/disk/by-uuid and only exists by-id and by-path, the udevd can't load blkid.

The bug is from initramfs-tools (0.92j)
at end of /usr/share/initramfs-tools/hooks/udev it does:
```
copy_exec /sbin/blkid /lib/modules
```
and it should do:
```
copy_exec /sbin/blkid /sbin
```
Once it's corrected remember to:
```
update-initramfs -u
```

Good luck
__________
M.Á.Ferrer

---

### Post by maferrer on 2010-06-18
If not exists /dev/disk/by-uuid and only exists by-id and by-path, the udevd can't load blkid.

The bug is from initramfs-tools (0.92j)
at end of /usr/share/initramfs-tools/hooks/udev it does:
```
copy_exec /sbin/blkid /lib/modules
```
and it should do:
```
copy_exec /sbin/blkid /sbin
```
Once it's corrected remember to:
```
update-initramfs -u
```

Good luck
__________
M.Á.Ferrer

---

