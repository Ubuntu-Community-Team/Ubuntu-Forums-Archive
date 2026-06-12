---
title: "apt-get install cannot exec /tmp/* files"
date: 2007-01-31
forum: Server Platforms
---

### Post by rocketfu on 2007-01-31
Every time I try to run apt-get dist-upgrade many of the upgrades fail with a

**Can't exec "/tmp/squid.config.38881": Permission denied at /usr/share/perl/5.8/IPC/Open3.pm.**

The same error occurs when I try to upgrade many applications. Are my user groups not defined correctly? Why can the system not access the /tmp/ folder?

Thanks in advance,
rocketfu

---

### Post by Nik_Doof on 2007-01-31
Is /tmp mounted as a seperate partition / drive / ram disk? If so it may have the noexec flag set in /etc/fstab.

---

### Post by rocketfu on 2007-01-31
I executed "cat /etc/fstab" as su

here is the output:

proc   /proc      proc     defaults    0    0
none  /dev/pts  devpts  rw           0    0

It does look like there is anything about no exec.

What do you think?

Thanks
--Rocketfu

---

### Post by rocketfu on 2007-01-31
No the /tmp/ folder is not on a different mount or disk

---

### Post by rocketfu on 2007-02-08
An update to this thread so hopefully resolve it. 

I executed the mount command and it looks like the mount does have a noexec on it.

Output from mount command:

/dev/vzfs on / type reiserfs (rw,usrquota,grpquota)
ext3 on /tmp type ext3 (rw,noatime,nosuid,nodev,noexec)
ext3 on /var/tmp type ext3 (rw,noatime,nosuid,nodev,noexec)
proc on /proc type proc (rw,nodiratime)
tmpfs on /var/run type tmpfs (rw)
tmpfs on /var/lock type tmpfs (rw)
devpts on /dev/pts type devpts (rw)
tmpfs on /dev/shm type tmpfs (rw)
tmpfs on /var/run type tmpfs (rw)
tmpfs on /var/lock type tmpfs (rw)

So I figure I have two options:

1. reconfigure apt-get to use a different folder for installation scripts
2. change the mount for the /tmp to make it exec

I tried to use 
mount -o remount,exec /tmp

but I get "mount: /tmp not mounted already, or bad option"

any ideas?

Thanks
rocketfu

---

