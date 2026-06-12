---
title: "Slow Boot running root from SSD on Pi 4"
date: 2020-02-18
forum: Server Platforms
---

### Post by trankin on 2020-02-18
I'm attempting to run Ubunto 19.10 on a Pi 4, but with the root FS on an SSD instead of from the SD card.  

I'm able to successfully run this way, but the boot is very slow and seems to hand a bit on startup.. but once it finishes, everything else in the system seems fine.

During boot, it appears to hang on Scanning for BTRFS filesystems.... but google searches for this didn't net much info.

I'm sure I've done something silly wrong, but it's not standing out for me.   I managed all of this by burning a copy of the ubuntu image to an SD card and the SSD.. then in /boot/nocmd.txt I changed the rootfs to my ssd.   Below is some information that I thought might be helpful if anyone had some time to help me troubleshoot..  Thanks for your consideration.

systemd-analyze
```

Startup finished in 3min 8.572s (kernel) + 14.524s (userspace) = 3min 23.096s
graphical.target reached after 11.782s in userspace

```

df
```

Filesystem     1K-blocks    Used Available Use% Mounted on
udev             1892236       0   1892236   0% /dev
tmpfs             388244    3688    384556   1% /run
/dev/sda2      461423932 3037460 439603416   1% /
tmpfs            1941204       0   1941204   0% /dev/shm
tmpfs               5120       0      5120   0% /run/lock
tmpfs            1941204       0   1941204   0% /sys/fs/cgroup
/dev/loop0         80896   80896         0 100% /snap/core/8042
/dev/loop1         82944   82944         0 100% /snap/core/8596
/dev/loop2         50176   50176         0 100% /snap/lxd/12634
/dev/loop3         61056   61056         0 100% /snap/lxd/13393
/dev/sda1         258095  129062    129033  51% /boot/firmware
tmpfs             388240       0    388240   0% /run/user/1001

```

blkid
```

/dev/sda1: LABEL_FATBOOT="system-boot" LABEL="system-boot" UUID="BB14-E4C0" TYPE="vfat" PARTUUID="d34db33f-01"
/dev/sda2: LABEL="writable" UUID="a136479c-fe8d-4a35-bed4-56fd88c3c07c" TYPE="ext4" PARTUUID="d34db33f-02"
/dev/mmcblk0p1: LABEL_FATBOOT="system-boot" LABEL="system-boot" UUID="BB14-E4C0" TYPE="vfat" PARTUUID="3d2c824d-01"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"

```

/etc/fstab
```

/dev/sda2       /        ext4   defaults        0 0
LABEL=system-boot       /boot/firmware  vfat    defaults        0       1

```

---

### Post by TheFu on 2020-02-18
I know ZERO about booting rpis, but have 2 here working with custom installs.

You have 2 partitions with the same LABEL and same UUID.  Don't do that. The fstab doesn't know which to use.

**df -Th** would be helpful. Shows the flle system types and "human" output.

**systemd-analyze critical-chain** would be more helpful for finding boot issues. What is posted above isn't related to when the system can be used, just when it is done with all initializations.

```
$ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/mmcblk0p7 ext4      2.5G  2.3G  139M  95% /
/dev/mmcblk0p6 vfat       79M   36M   44M  46% /boot
```
are the interesting parts on my pi v3. Note that /boot/ is the mount point. That is expected, not /boot/firmware

[https://www.raspberrypi.org/documentation/configuration/boot_folder.md](https://www.raspberrypi.org/documentation/configuration/boot_folder.md)

But I don't know anything.

---

### Post by trankin on 2020-02-19
I worked this a bit more and have cleaned up my partitions.   I deleted /dev/sda1 which had the conflicting UUID with the sd card, doesn't seem to have affected anything.  

I uninstalled btrfs-progs ```
[COLOR=#242729][FONT=Consolas]apt purge btrfs-progs
``` 
[/FONT][/COLOR]This gives me a new message at boot time that shows me that the code that is hanging is /scripts/local-premount which seems to be related to initramfs.

I've read a few things related to this and followed a few instructions to disable RESUME, but nothing seems to have had effect.

I'll keep dinking, after boot everything seems to run fine, but boot takes a few minutes.  So it's nothing awful but inconvenient.





> **TheFu said:**
> I know ZERO about booting rpis, but have 2 here working with custom installs.

You have 2 partitions with the same LABEL and same UUID.  Don't do that. The fstab doesn't know which to use.

**df -Th** would be helpful. Shows the flle system types and "human" output.

**systemd-analyze critical-chain** would be more helpful for finding boot issues. What is posted above isn't related to when the system can be used, just when it is done with all initializations.

```
$ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/mmcblk0p7 ext4      2.5G  2.3G  139M  95% /
/dev/mmcblk0p6 vfat       79M   36M   44M  46% /boot
```
are the interesting parts on my pi v3. Note that /boot/ is the mount point. That is expected, not /boot/firmware

[https://www.raspberrypi.org/documentation/configuration/boot_folder.md](https://www.raspberrypi.org/documentation/configuration/boot_folder.md)

But I don't know anything.

---

