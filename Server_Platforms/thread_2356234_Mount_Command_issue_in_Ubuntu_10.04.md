---
title: "Mount Command issue in Ubuntu 10.04"
date: 2017-03-21
forum: Server Platforms
---

### Post by aristatechnologies2 on 2017-03-21
Hello,

I am running Ubuntu 10.04 since last 7 year on HP Server and it was working fine.

All of sudden the disk space started deplating (reducing) day by day.

So I ran one command #mount
and below is the output

/dev/cciss/c0d0p1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda1 on /mnt/usbbu type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/cciss/c0d1p1 on /media/file_server type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dcap/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dcap)
gvfs-fuse-daemon on /home/prod/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=prod)



So is there any issue with the system?
How to find out where the space is getting used?
I ran lots of command like #du -sh and in different combination to find  out the exact size but somehow I find something fishy happening.

Can someone point out how to find exact cause of this.

---

### Post by howefield on 2017-03-21
Thread moved to the "*Server Platforms*" forum, for a better fit.

I'm sure you know that 10.04 has long since expired, deceased, and is no more a good choice of system.

---

### Post by aristatechnologies2 on 2017-03-21
Thanks for helping in moving thread to right location.

But right now cannot change the server because lots of things are depedant on it.

so if someone can help in this regard it would be great.

---

### Post by alexandari on 2017-03-21
Well I guess there is a log somewhere that writes to the disk. You can see what is currently writing to the disk using a tool called fatrace

```
sudo apt-get install fatrace
```

then just type fatrace review the information that is giving. 

Another thing you can run to see which directory takes a certain amount of disk space is

```
 du -h --max-depth=1 
```

---

### Post by darkod on 2017-03-21
Well, that doesn't really help us much. Can you post the output of following commands
```
df -h
cd /
du -sh *
cd /media/file_server
du -sh *
```

You should know better than us how much free/used space to expect for your media.

Also if you see / filling up strangely one thing that can happen is if at any time the media mount failed. In such case data will start to get written at the same media path but on the partition that is for root, not for media. You can check this by unmounting media and check the same path on root partition. It should be empty.

---

