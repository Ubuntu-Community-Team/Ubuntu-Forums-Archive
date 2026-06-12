---
title: "External drive not automounting"
date: 2011-07-16
forum: Server Platforms
---

### Post by Comrie19 on 2011-07-16
I have a home server running from a Kubuntu install. I am using a partitioned external hard drive to store media. I have been suffering from power outages and I have discovered my external drive will not automount. Below is my mtab file and sdc1 is my external drive. How do I get my drive to mount at boot?

/dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
/dev/mapper/VG1-LV1 /home/user/share ext2 rw 0 0
/dev/sdc1 /VIDEOS ext4 rw 0 0

---

### Post by ankspo71 on 2011-07-16
Hi,
I believe it would be the same way as how people mount secondary internal drives, which is what I have been doing.

First you need to create a mountpoint so you can mount the drive to a specific location. 
(a mountpoint is just a normal directory, but it is used as a place to mount partitions)

Open your terminal and paste the following:
```
sudo mkdir /media/sdc1
```
Then enter your password.
That command will create a directory named "sdc1" in your /media folder.

Now you can modify your /etc/fstab file so that the external drive automounts:
Open a terminal and paste this:
```
kdesudo kate /etc/fstab
```
Now look for your sdc1 drive entry (if any) and modify it like this:
```
/dev/sdc1 /media/sdc1 ext4 users 0 0
```
"users" is the mount option that will make it automount at startup.

Note: I think your external drive will need to be turned on before you start Kubuntu though, because if Kubuntu can't find the drive it might prevent or delay Kubuntu from starting.

Mounting with UUID numbers:
If you have more than one storage partition and you start to experience your partitions being mounted in the wrong mountpoints, then you can use UUIDs to mount the partitions to prevent that from happening:

Open a terminal and type:
```
sudo blkid
```
Now find the UUID number for your external drive.
Now open the fstab file again: 
```
kdesudo kate /etc/fstab
```
Then replace the device name "/dev/sdc1" with the UUID like this:
```
UUID=7232a4f9-6a2e-46ad-be17-f05246e6729d /media/sdc1 ext4 users 0 0
```

Hope this helps.

---

### Post by Comrie19 on 2011-07-16
ty ankspo71,

I had a directory (/VIDEOS) created as a mount point.

Added "/dev/sdc1 /VIDEOs ext4 rw 0 0" to fstab and it seems to have mounted at boot. I was having issues with partitions mounting in wrong order so the UUID tip will help me a lot. Hopefully this continues to work. Thank you for the help.

---

### Post by ankspo71 on 2011-07-16
Hi again,
I think if you have ownership of all of the files on the drive (including the mountpoint), then mounting with the "rw" mount option should work fine. I think the "users" mount option helps if the files and directories on the drive are still owned by root.

---

