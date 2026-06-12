---
title: "external HDD path, server 10.10"
date: 2011-01-19
forum: Server Platforms
---

### Post by JeremyTheLee on 2011-01-19
[LEFT][/LEFT]I'm new to using the ubuntu server OS, so try to bear with me. 


I've got samba up and running, and i'm trying to set the share path to an external hdd. I ran ubuntu netbook off my thumb drive just to get the path directory for the external, and it was presented as /media/6C8AC7868AC77ADA. however, when I input the path to make sure it is accessible, I get this;


```
jeremy@Jeremy-LinuxShare:~$ /media/6C8AC7868AC77ADA/
-bash: /media/6C8AC7868AC77ADA/: No such file or directory

```


I feel like I must be making a simple mistake, but I can't figure it out myself. I've been at it off and on for a few days now, and decided you guys might be my best bet.



EDIT: I've tried the lsusb command and mount, but i'm not sure any of the information they give me I can use to find the path of my external HDD. 

```
jeremy@Jeremy-LinuxShare:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1058:1110 Western Digital Technologies, Inc.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
```
jeremy@Jeremy-LinuxShare:~$ mount
/dev/mapper/Jeremy--LinuxShare-root on / type ext4 (rw,errors=remount-ro)
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
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
/dev/sda1 on /boot type ext2 (rw)
/home/jeremy/.Private on /home/jeremy type ecryptfs (ecryptfs_sig=76ee800427fafb9d,ecryptfs_fnek_sig=8af0f3c44d32daf5,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
```

---

### Post by psusi on 2011-01-19
Server does not automatically mount external media.  You will need to do that yourself.

---

### Post by arrrghhh on 2011-01-19
> **psusi said:**
> Server does not automatically mount external media.  You will need to do that yourself.

Indeed.

So to the OP - if the hard disk is always plugged in, I would add an entry in fstab for it.

```
sudo nano /etc/fstab
```

See the Ubuntu Community Page on [Fstab](https://help.ubuntu.com/community/Fstab).

To find the UUID of the disk (which it seems like you already have), ```
ls -lah /dev/disk/by-uuid
```

---

