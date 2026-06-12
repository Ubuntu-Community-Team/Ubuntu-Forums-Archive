---
title: "Building Ubuntu sources under VirtualBox"
date: 2012-08-23
forum: Virtualisation
---

### Post by gosetos on 2012-08-23
Hi,
 

I need to buid and run Ubuntu kernel under VirtualBox from the sources you can get from kernel.org. I'm a newby in the process of such a task. What I've done so far is:
[LIST]
[*]I have already a Ubuntu image running on my VirtualBox (my host OS is Windows 7).
[*]I downloaded the Ubuntu kernel sources from kernel.org (v3.5.2).
[*]Under /usr/src/linux3.5.2/
[/LIST]"make menuconfig"
"make bzImage"
"cp arch/x86/boot/bzImage /boot/vmlinuz"

"sudo reboot"
[LIST]
[*]Then it restarts and I get the following error when booting:
[/LIST]EXT3-fs (sda1): error: couldn't mount because of unsupported optional features (240)
 
See the attached screenshot. I guess I'm missing something regarding file system config, any tips please?
 
Thank you

---

### Post by gosetos on 2012-08-23
Forgot to mention I also do "make install"

---

### Post by gosetos on 2012-08-23
Execution of command "mount" gives the output:
 
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
shared on /media/sf_shared type vboxsf (gid=1001,rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/deinluro/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=deinluro)
/dev/sr0 on /media/VBOXADDITIONS_4.1.8_75467 type iso9660 (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=0,iocharset=utf8,mode=0400,dmode=0500)

---

