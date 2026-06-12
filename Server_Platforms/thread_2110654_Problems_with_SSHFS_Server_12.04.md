---
title: "Problems with SSHFS Server 12.04"
date: 2013-01-30
forum: Server Platforms
---

### Post by fhovie on 2013-01-30
Greetings: I manage several servers in several locations all running Ubuntu Server 64bit. I have been trying to remotely mount a share from one location on another location and seem to hit a wall. It seems like the remote share mounts but I cannot seem to access it. Here is a snip:

frank@aaa-ventura:/mnt$ sudo sshfs -o idmap=user frank@myremoteserver.net:/mnt/allback /mnt/remoteserv/
frank@myremoteserver.net's password:

looked like it mounted fine

frank@aaa-ventura:/mnt$ ls -hal
ls: cannot access remoteserv: Permission denied
total 12K
drwxr-xr-x  4 root root 4.0K Jan 30 13:23 .
drwxr-xr-x 24 root root 4.0K Jan  8 12:54 ..
drwxrwxrwx  5 root root 4.0K Jan  8 16:43 allback
d?????????  ? ?    ?       ?            ? remoteserv

mounted volume not accessable

frank@aaa-ventura:/mnt$ sudo mount
/dev/md0 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sdc1 on /mnt/allback type ext4 (rw)
frank@myremoteserver.net:/mnt/allback on /mnt/remoteserv type fuse.sshfs (rw,nosuid,nodev,max_read=65536)

Looks like it mounted properly .. any ideas? thanks

---

### Post by tgalati4 on 2013-01-30
```
cat /var/log/auth.log
```

I presume you have the same username on all of the machines?  Do you need the sudo command to make the mount?

---

