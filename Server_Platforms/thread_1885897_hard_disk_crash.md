---
title: "hard disk crash?"
date: 2011-11-24
forum: Server Platforms
---

### Post by chrpinedo on 2011-11-24
Hello all,

I have the latest version of Ubuntu Server 11.10 x64 with all patches running in a small PC Foxconn with a 2,5'' SATA hard disk.

The systems had been working ok for 1 month since the instalation. But since this week every 24-48 hours the system crahses.

```
 root@perfserv1:~# /sbin/fdisk -l
-bash: /sbin/fdisk: Error de entrada/salida (Input/Output error)
root@perfserv1:~# reboot
-bash: /sbin/reboot: Error de entrada/salida (Input/Output erro)
root@perfserv1:~# LANG=C mount
/dev/mapper/SYSvg-ROOTlv on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda1 on /boot type ext4 (rw)
/dev/mapper/SYSvg-TMPlv on /tmp type ext4 (rw)
/dev/mapper/SYSvg-HOMElv on /home type ext4 (rw)
/dev/mapper/SYSvg-VARlv on /var type ext4 (rw)
/dev/mapper/SYSvg-USRlv on /usr type ext4 (rw)

mount: warning: /etc/mtab is not writable (e.g. read-only filesystem).
       It's possible that information reported by mount(8) is not
       up to date. For actual information about system mount points
       check the /proc/mounts file.
```
If I run dmesg I can see a lot of errors:

```
[87780.141885] EXT4-fs (dm-2): previous I/O error to superblock detected
[87780.145868] sd 0:0:0:0: [sda] Unhandled error code
[87780.145876] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[87780.145887] sd 0:0:0:0: [sda] CDB: Write(10): 2a 00 00 d8 29 80 00 00 08 00
[87780.145913] end_request: I/O error, dev sda, sector 14166400
[87780.149817] Buffer I/O error on device dm-2, logical block 0
[87780.153685] lost page write due to I/O error on dm-2
[87780.153741] EXT4-fs error (device dm-2): ext4_find_entry:934: inode #2: comm cron: reading directory lblock 0
[87792.955007] sd 0:0:0:0: [sda] Unhandled error code
[87792.955021] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[87792.955034] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 01 14 b4 b0 00 00 08 00
[87792.955063] end_request: I/O error, dev sda, sector 18134192
[87803.793864] sd 0:0:0:0: [sda] Unhandled error code
[87803.793878] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[87803.793891] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 00 0c 57 80 00 00 08 00
[87803.793919] end_request: I/O error, dev sda, sector 808832
[87803.798038] sd 0:0:0:0: [sda] Unhandled error code
[87803.798046] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[87803.798057] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 00 0c 57 80 00 00 08 00
[87803.798082] end_request: I/O error, dev sda, sector 808832
[87808.889902] sd 0:0:0:0: [sda] Unhandled error code
[87808.889917] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[87808.889929] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 00 0c 57 80 00 00 08 00
[87808.889957] end_request: I/O error, dev sda, sector 808832
[87808.893912] sd 0:0:0:0: [sda] Unhandled error code
[87808.893917] sd 0:0:0:0: [sda]  Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
[87808.893923] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 00 0c 57 80 00 00 08 00
[87808.893935] end_request: I/O error, dev sda, sector 808832
```The hard disk is 2,5". I use LVM. 

It is a bug of the OS or a the hard disk is broken. How can I find out????

Thanks,

Christian

---

### Post by volkswagner on 2011-11-24
Boot the system using a live CD such as Ubuntu Desktop.

You can run badblocks  against the hard drive to see if there are bad blocks.

```
man badblocks
```

---

