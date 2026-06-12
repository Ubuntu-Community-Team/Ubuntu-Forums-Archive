---
title: "Cannot write to drive using GUID/ext4"
date: 2011-11-07
forum: Ubuntu Studio
---

### Post by RedCell989 on 2011-11-07
Using Ubuntu Studio 11.04 with 11.10 Ubuntu updates, I have a Seagate 1TB SATA 2 drive that I formatted using GUID partition table, and ext4 file system. Problem is, it now says I am not the owner of the drive, and wont give me write permissions, so all I can do is read files (its blank so far). Is this common for GUID? how do I become the owner or get permissions?

Thanks!

---

### Post by jejeman on 2011-11-07
How did you mounted it?
Give us output from
```
mount
```

---

### Post by oldfred on 2011-11-07
gpt(GUID) or MBR(msdos) has nothing to do with it. It is just ownership and permissions.

Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

Manually mount it one time(or each time you reboot). Note 777 is the most permissive, which you may not want if multiuser.

sudo mkdir /mnt/data
sudo chmod 777 /mnt/data
sudo chown $USER:$USER /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
#if not known to list partitions
sudo fdisk -l

---

### Post by RedCell989 on 2011-11-07
I am not too comfortable in terminal (recently switched from windows) so I just used the desktop unity sidebar and clicked on "home folder" then it shows me a list of devices even if they have not been mounted yet, and when I click on any unmounted device in the list it mounts it for me. Here is the output from "mount" command in terminal:

```
darkfears@DarkFears:~$ mount
/dev/sda4 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sdc1 on /media/Monster type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/darkfears/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=darkfears)
/dev/sdb1 on /media/90eeef9f-25ca-4fbb-b4ad-ec23efc29faa type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1 on /media/HP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2 on /media/FACTORY_IMAGE type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
darkfears@DarkFears:~$ 
```

I thought it might have to do with the gtp aspect because before I reformatted to gtp (using gparted) I had formatted the drive with the msdos/mbr partition table and it automatically gave me ownership/permissions.

---

### Post by RedCell989 on 2011-11-07
btw fdisk tells me: WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted

---

### Post by oldfred on 2011-11-07
No you do not use fdisk with gpt partitioning. You can use parted, gparted or download and use gdisk with is fdisk for gpt drives.

---

### Post by RedCell989 on 2011-11-08
Ahh well I tried those methods and nothing was giving me write access, or would give me write access but not delete access, or was only allowing me to write new files and not allowing write access to existing files. I ended up reformatting the drive with msdos/mbr partition table and ext4 file system. Everything works just fine after I switched back to mbr.

---

