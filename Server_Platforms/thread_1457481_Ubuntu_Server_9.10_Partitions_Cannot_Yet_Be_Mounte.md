---
title: "Ubuntu Server 9.10 Partitions Cannot Yet Be Mounted"
date: 2010-04-18
forum: Server Platforms
---

### Post by eschnell on 2010-04-18
I have been searching around trying to find the problem I am having, and have found some like it, but none of solutions fix mine. After installing the asterisk-addons package onto my server, I told it to restart, and I come back and find this in the screen:

> fsck from util-linux-ng 2.16
/dev/sda5: clean, 170/124496 files, 43271/248976 blocks
* Stopping NTP server ntpd
* Could not access PID file for nmbd
One or more of the mounts listed in /etc/fstab cannot yet be mounted:
(ESC for recovery shell)
/: waiting for /dev/mapper/server-root
/tmp: waiting for (null)
/boot: waiting for /dev/sda5
* Starting NTP server ntpdAfter pressing ESC for the recovery shell, I get this:

> mountall: Canceled
init: mountall main process (423) terminated with status 1
General error mounting filesystem
Ctrl+D to exit
root@server#blkid:

> /dev/sda1: UUID="..." type="LVM2_mem???"
/dev/sda5: UUID="..." type="ext2"
/dev/mapper/server-swap_1 UUID="..." type="swap"fstab

> proc     /proc     proc     defaults     0     0
/dev/mapper/server-root     /     ext4     errors=remount-ro     0     1
/dev/sda5     /boot     ext2     defaults     0     2
/dev/mapper/server-swap_1     none     swap     sw     0     0
/dev/scd0 ...
/dev/fd0 ...Note: The /dev/sda5 line used to have UUID="...."

fsck on /dev/sda5 and /dev/mapper/server-root come up clean

Help please!

Thanks,
Eddie

---

