---
title: "/tmp and Virtual Memory Question"
date: 2012-08-29
forum: Server Platforms
---

### Post by jnichols51 on 2012-08-29
I am a little confused about Virtual Memory, Swap, and the /tmp folder. I did a stock install of Ubuntu server on a system that only has about 1GB. I installed Webmin and needed to do an update. It failed because it said my /tmp dir was too full. I check and it appeared that /tmp was using RAM/Swap Disk and was limited to only 1024 Kb. I searched and found some docs and used Webmin to up the amount to 100Mb, but it couldn't mount it because it was in use. So I was able to save it and rebooted. 

Now I appear to have a /tmp that is 100Mb in size, but it appears that my Virtual Memory is gone. My home screen shows this:

**Real memory** 938.01 MB total, 121.94 MB used
**Virtual memory** 1.42 GB total, 0 bytes used
**Local disk space** 1.60 TB total, 205.66 GB used

And my Disk and Network Filesystems tab looks like this:

**Mounted as** Type
**Location** 
**Used** 
**In use?** 
**Saved?**    /proc Kernel Filesystem (proc) proc 
[Yes]("https://norad-server:10000/mount/unmount.cgi?index=1") Yes   [/ (*Root filesystem*)]("https://norad-server:10000/mount/edit_mount.cgi?index=1") New Linux Native Filesystem (ext4) LVM VG mapper, LV NORAD--SERVER-root 15% [Yes]("https://norad-server:10000/mount/unmount.cgi?index=0") Yes   [/boot]("https://norad-server:10000/mount/edit_mount.cgi?index=2") Old Linux Native Filesystem (ext2) Partition with ID afd04771-882d-48a6-9ac3-10507241686a 87% [Yes]("https://norad-server:10000/mount/unmount.cgi?index=11") Yes   [*Virtual Memory*]("https://norad-server:10000/mount/edit_mount.cgi?index=3") Virtual Memory (swap) LVM VG mapper, LV NORAD--SERVER-swap_1 
[[COLOR=#ff0000]No[/COLOR]]("https://norad-server:10000/mount/mount.cgi?index=3") Yes   /media/floppy0 Unknown Type Floppy disk 0 
[[COLOR=#ff0000]No[/COLOR]]("https://norad-server:10000/mount/mount.cgi?index=4") Yes   [/mnt/ide_drive1]("https://norad-server:10000/mount/edit_mount.cgi?index=5") Linux Native Filesystem (ext3) SATA device A partition 1 33% [Yes]("https://norad-server:10000/mount/unmount.cgi?index=12") Yes   [/tmp]("https://norad-server:10000/mount/edit_mount.cgi?index=6") RAM/Swap Disk (tmpfs) tmpfs 0% [Yes]("https://norad-server:10000/mount/unmount.cgi?index=14") Yes   /sys Kernel Filesystem (sysfs) sysfs 
[Yes]("https://norad-server:10000/mount/unmount.cgi?index=2") [COLOR=#ff0000]No[/COLOR]   ... /fs/fuse/connections FUSECTL none 
[Yes]("https://norad-server:10000/mount/unmount.cgi?index=3") [COLOR=#ff0000]No[/COLOR]   /sys/kernel/debug DEBUGFS none 
[Yes]("https://norad-server:10000/mount/unmount.cgi?index=4") [COLOR=#ff0000]No[/COLOR]   /sys/kernel/security SECURITYFS none 
[Yes]("https://norad-server:10000/mount/unmount.cgi?index=5") [COLOR=#ff0000]No[/COLOR]   /dev RAM/Swap Disk (devtmpfs) udev 0% [Yes]("https://norad-server:10000/mount/unmount.cgi?index=6") [COLOR=#ff0000]No[/COLOR]   /dev/pts Pseudoterminal Device Filesystem (devpts) devpts 
[Yes]("https://norad-server:10000/mount/unmount.cgi?index=7") [COLOR=#ff0000]No[/COLOR]   [/run]("https://norad-server:10000/mount/edit_mount.cgi?temp=1&index=8") RAM/Swap Disk (tmpfs) tmpfs 0% [Yes]("https://norad-server:10000/mount/unmount.cgi?index=8") [COLOR=#ff0000]No[/COLOR]   [/run/lock]("https://norad-server:10000/mount/edit_mount.cgi?temp=1&index=9") RAM/Swap Disk (tmpfs) none 0% [Yes]("https://norad-server:10000/mount/unmount.cgi?index=9") [COLOR=#ff0000]No[/COLOR]   [/run/shm]("https://norad-server:10000/mount/edit_mount.cgi?temp=1&index=10") RAM/Swap Disk (tmpfs) none 0% [Yes]("https://norad-server:10000/mount/unmount.cgi?index=10") [COLOR=#ff0000]No[/COLOR]   [/media/usb0]("https://norad-server:10000/mount/edit_mount.cgi?temp=1&index=13") New Linux Native Filesystem (ext4) SCSI device C partition 1 9% [Yes]("https://norad-server:10000/mount/unmount.cgi?index=13") [COLOR=#ff0000]No[/COLOR]   [*Virtual Memory*]("https://norad-server:10000/mount/edit_mount.cgi?temp=1&index=15") Virtual Memory (swap) /dev/dm-1 
[Yes]("https://norad-server:10000/mount/unmount.cgi?index=15") [COLOR=#ff0000]No[/COLOR]       
  I think that last Virtual Memory entry was put in because I tried to turn the first Virtual Memory entry on.

I just want to make sure that Apache and MySQL will run as fast as they can and that I don't crash the server by running out of memory. The server is just being used a home server so I can learn this stuff. How do I make sure that Vitual Memory is setup correctly along with Swap and /tmp?

---

### Post by Bachstelze on 2012-08-29
Post the output of [font=monospace]mount[/font].

---

### Post by jnichols51 on 2012-10-24
/dev/mapper/XXXXX--SERVER-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /tmp type tmpfs (rw,mode=1777,size=104857600)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdc1 on /media/usb0 type ext4 (rw,noexec,nodev,sync,noatime,nodiratime,user_xattr,barrier=1,data=ordered)
/dev/sdb1 on /boot type ext2 (rw)
/dev/sda1 on /mnt/ide_drive1 type ext3 (rw)
/dev/sdc1 on /var/lib/backuppc type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

---

