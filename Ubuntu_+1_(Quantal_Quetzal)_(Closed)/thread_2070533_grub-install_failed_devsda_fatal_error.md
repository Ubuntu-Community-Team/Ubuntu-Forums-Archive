---
title: "grub-install failed /dev/sda fatal error"
date: 2012-10-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by elliotn on 2012-10-13
I installed Ubuntu 12.10 alpha 2 and got this problem at the end of d installation. I now sit with an installed Ubuntu with no bootloader..... I tried millions of times from other liveCD of ubuntu 10.10 12.04 to reinstall grub but still grub won't install. anyone help plz

---

### Post by elliotn on 2012-10-13
no help

---

### Post by lemming465 on 2012-10-13
I get the best results in these scenarios by using a live CD that matches the new install, combined with chroot.  E.g.

0. Ideally, update your live boot media to something more recent than alpha2 first; if bandwidth is an issue, try using zsync and a daily image from cdimage.ubuntu.com.  Write back if you need more directions for that.

1. Boot your 12.10 live media, and open a terminal window

2. Run *sudo fdisk -lu* or *sudo parted -l* to see what the device names and partition numbers are.  I'll assume your Linux root partition is /dev/sda3 in what follows; adjust as necessary.

3. Mount the root and/or boot partitions of the new install, starting with root. e.g. ```
sudo -i
mkdir /fixme
mount /dev/sda3 /fixme
```

4. Prep a chroot environment, still all as root```
cd /fixme
for fs in proc sys dev; do
  mkdir $fs
  mount -o bind /$fs $fs
done
chroot .
```
If /boot is a separate mount point, you'll need to do something about that now, e.g. *mkdir /boot; mount /dev/sdaXX /boot*.

5. Now fix grub.  I'm assuming you want it on that MBR of the first disk```
grub-install /dev/sda
```

---

### Post by grahammechanical on 2012-10-13
The best that I can offer is this link

[http://www.gnu.org/software/grub/grub-documentation.html]("http://www.gnu.org/software/grub/grub-documentation.html")

A lot depends on the partitioning table scheme used by windows 7. You are using 12.10 Alpha and that uses Grub 1.99. Whereas 12.10 now uses Grub 2.0. and there are differences. Grub 2.0 might be able to cope better with the partitioning table schemes of Windows 7 than Grub 1.99 does.

See this link for the issues with dual booting with Windows 7 and Grub 1.99

[http://ubuntuforums.org/showthread.php?t=2070332]("http://ubuntuforums.org/showthread.php?t=2070332")

Regards.

---

### Post by elliotn on 2012-10-14
> **lemming465 said:**
> i get the best results in these scenarios by using a live cd that matches the new install, combined with chroot.  E.g.
```

```
0. Ideally, update your live boot media to something more recent than alpha2 first; if bandwidth is an issue, try using zsync and a daily image from cdimage.ubuntu.com.  Write back if you need more directions for that.

1. Boot your 12.10 live media, and open a terminal window

2. Run *sudo fdisk -lu* or *sudo parted -l* to see what the device names and partition numbers are.  I'll assume your linux root partition is /dev/sda3 in what follows; adjust as necessary.

3. Mount the root and/or boot partitions of the new install, starting with root. E.g. ```
sudo -i
mkdir /fixme
mount /dev/sda3 /fixme
```

4. Prep a chroot environment, still all as root```
cd /fixme
for fs in proc sys dev; do
  mkdir $fs
  mount -o bind /$f $f
done
chroot .
```
if /boot is a separate mount point, you'll need to do something about that now, e.g. *mkdir /boot; mount /dev/sdaxx /boot*.

5. Now fix grub.  I'm assuming you want it on that mbr of the first disk

here is what i get after follwing your direction... My ubuntu is in /dev/sda5
```
grub-install /dev/sda
```buntu@ubuntu:~$ sudo -i
root@ubuntu:~# mkdir /fixme
mkdir: Cannot create directory `/fixme': File exists
root@ubuntu:~# mount /dev/sda5 /fixme
root@ubuntu:~# cd /fixme
root@ubuntu:/fixme# for fs in proc sys dev; do
>   mkdir $fs
>   mount -o bind /$f $f
> done
mkdir: Cannot create directory `proc': File exists
mount: Special device overlayfs does not exist
mkdir: Cannot create directory `sys': File exists
mount: Special device overlayfs does not exist
mkdir: Cannot create directory `dev': File exists
mount: Special device overlayfs does not exist
root@ubuntu:/fixme# chroot
chroot: Missing operand
try `chroot --help' for more information.
Root@ubuntu:/fixme# 
1

---

### Post by swissinvestor on 2012-10-14
[http://wiki.ubuntuusers.de/GRUB_2/Reparatur](http://wiki.ubuntuusers.de/GRUB_2/Reparatur)

Sorry, it's German but if you run it through a translator it should be no problem. I
I had a broken Grub2 but with copy/paste from this "how to repair Grub2" I could fix the problem within minutes. I had to use the Live DVD as I was unable to start the system at all.

---

### Post by lemming465 on 2012-10-15
Sorry, at step 4 that should have been:```
cd /fixme
for fs in proc sys dev ; do
  mkdir $fs
  mount -o bind /$fs $fs
done
chroot .
```

Note: the "." in "chroot ." matters; alternatively one could do "chroot /fixme".  That's the directory name, not punctuation.

---

### Post by fab.head on 2012-10-15
> **elliotn said:**
> I installed Ubuntu 12.10 alpha 2 and got this problem at the end of d installation. I now sit with an installed Ubuntu with no bootloader..... I tried millions of times from other liveCD of ubuntu 10.10 12.04 to reinstall grub but still grub won't install. anyone help plz

Could it be that you installed Ubuntu in BIOS/MBR mode on an EFI/GPT system?

A similar error happened to me some time ago on a UX31A: I didn't select UEFI at boot (by mistake), and at the end of the installation I got the very same error message (and no GRUB installed).

I then rebooted with the Escape key pressed to change the boot order (on your computer it may be a different key, e.g. F9 or something else) and set the system to boot from a USB stick in UEFI mode. The installation was just fine then.

---

### Post by elliotn on 2012-10-16
> **lemming465 said:**
> Sorry, at step 4 that should have been:```
cd /fixme
for fs in proc sys dev ; do
  mkdir $fs
  mount -o bind /$fs $fs
done
chroot .
```

Note: the "." in "chroot ." matters; alternatively one could do "chroot /fixme".  That's the directory name, not punctuation.

chroot: failed to run command '/bin/bash' : No such file or directory

---

### Post by lemming465 on 2012-10-16
What does```
df -m
cat /proc/mounts
ls /fixme
```
show after the *mount /dev/sdXX* in step 3?

---

### Post by lemming465 on 2012-10-16
Output from **parted -l** would also be good to have.

---

### Post by elliotn on 2012-10-17
> **lemming465 said:**
> What does```
df -m
cat /proc/mounts
ls /fixme
```
show after the *mount /dev/sdXX* in step 3?

```
 root@ubuntu:~# df -m
Filesystem     1M-blocks  Used Available Use% Mounted on
/cow                1002    42       960   5% /
udev                 992     1       992   1% /dev
tmpfs                401     1       400   1% /run
/dev/sr0             751   751         0 100% /cdrom
/dev/loop0           714   714         0 100% /rofs
tmpfs               1002     1      1002   1% /tmp
none                   5     1         5   1% /run/lock
none                1002     1      1002   1% /run/shm
none                 100     1       100   1% /run/user
/dev/sda6          47749  2534     42791   6% /fixme
root@ubuntu:~# cat /proc/mounts
rootfs / rootfs rw 0 0
sysfs /sys sysfs rw,nosuid,nodev,noexec,relatime 0 0
proc /proc proc rw,nosuid,nodev,noexec,relatime 0 0
udev /dev devtmpfs rw,relatime,size=1015308k,nr_inodes=253827,mode=755 0 0
devpts /dev/pts devpts rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000 0 0
tmpfs /run tmpfs rw,nosuid,relatime,size=410168k,mode=755 0 0
/dev/sr0 /cdrom iso9660 ro,noatime 0 0
/dev/loop0 /rofs squashfs ro,noatime 0 0
tmpfs /cow tmpfs rw,noatime,mode=755 0 0
/cow / overlayfs rw,relatime,lowerdir=//filesystem.squashfs,upperdir=/cow 0 0
none /sys/fs/fuse/connections fusectl rw,relatime 0 0
none /sys/kernel/debug debugfs rw,relatime 0 0
none /sys/kernel/security securityfs rw,relatime 0 0
tmpfs /tmp tmpfs rw,nosuid,nodev,relatime 0 0
none /run/lock tmpfs rw,nosuid,nodev,noexec,relatime,size=5120k 0 0
none /run/shm tmpfs rw,nosuid,nodev,relatime 0 0
none /run/user tmpfs rw,nosuid,nodev,noexec,relatime,size=102400k,mode=755 0 0
gvfsd-fuse /run/user/ubuntu/gvfs fuse.gvfsd-fuse rw,nosuid,nodev,relatime,user_id=999,group_id=999 0 0
/dev/sda6 /fixme ext4 rw,relatime,data=ordered 0 0
root@ubuntu:~# ls /fixme
bin    dev   initrd.img      lib64       mnt   root  selinux  tmp  vmlinuz
boot   etc   initrd.img.old  lost+found  opt   run   srv      usr
cdrom  home  lib             media       proc  sbin  sys      var
root@ubuntu:~# 
 
```

that is what I get

---

### Post by elliotn on 2012-10-17
firstly when I installed ubuntu was on /dev/sda1 then I reinstalled and it changed to /dev/sda5 and now I c its in /dev/sda6. what's going on

---

### Post by lemming465 on 2012-10-17
> **elliotn said:**
> firstly when I installed ubuntu was on /dev/sda1 then I reinstalled and it changed to /dev/sda5 and now I c its in /dev/sda6. what's going on

Ok, this is where the output of ```
sudo -i
parted -l
blkid
```
may help us.

When you ran your various install tries, what kind of disk partitioning choices did you make?  Manual, automatic, share with existing?  If you made multiple choices you might end up with multiple partitions.  

A scarier possibility is that you have some lingering fake RAID setup, and windows and Linux have different and conflicting opinions about the disk geometry.  That scenario tends to result in catastrophic disk partition damage to filesystems, and mostly ends up with wiping the first 10 MB of the disk with zeroes using *dd*, then reinstalling everything from scratch.

In multiboot scenarios with multiple operating systems I personally get the best results from (1) start partitioning with windows 7, to get modern partition alignments  (2) finish partitioning with Linux, to get the partition ID's and extended partition layout right [assuming BIOS disks, not GPT disks] (3) install windows, since it will tromp on the disk MBR (4) install Linux.  Who owns the boot process and the MBR varies; usually I have grub2 do that, but if I'm using disk encryption with windows I use EasyBCD from neosmart to chain to grub2 located on the linux root partition instead.

---

### Post by elliotn on 2012-10-17
matter solved by deleting the swap and the Ubuntu partition and recreating them and it worked

---

