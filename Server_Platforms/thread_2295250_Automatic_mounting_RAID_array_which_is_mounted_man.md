---
title: "Automatic mounting RAID array which is mounted manually."
date: 2015-09-17
forum: Server Platforms
---

### Post by akshay-sulakhe on 2015-09-17
Hello friends,

For our server setup, we have a RAID array which is being setup once and we have actually never rebooted the server. Right now the array is working fine, but I would like to add its entry to fstab so it's mounted automatically. I just don't know how to do that, as I can see the entry in mdadm.conf. The raid array is mounted on /dev/md1. 

Output of mount command :
```

sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,relatime,size=10240k,nr_inodes=4108136,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=3287872k,mode=755)
/dev/disk/by-uuid/ae73679c-c3cd-4a60-bcbb-5b6ddce867f7 on / type ext4 (rw,relatime,user_xattr,barrier=1,data=ordered)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /run/shm type tmpfs (rw,nosuid,nodev,noexec,relatime,size=9931180k)
/dev/sdc2 on /boot type ext3 (rw,relatime,errors=continue,user_xattr,acl,barrier=1,data=ordered)
/dev/md1 on /media/attachment type ext4 (rw,relatime,user_xattr,barrier=1,stripe=256,data=ordered)
```


Contents of /etc/fstab file :

```
proc /proc proc defaults 0 0
# /dev/sdc1 during Installation (RescueSystem)
UUID=b678077b-314c-4e2f-84ed-a3d0b3ded812 none swap sw 0 0
# /dev/sdc2 during Installation (RescueSystem)
UUID=12c0304a-21cc-4b4b-ac35-2352766620b3 /boot ext3 defaults 0 0
# /dev/sdc3 during Installation (RescueSystem)
UUID=ae73679c-c3cd-4a60-bcbb-5b6ddce867f7 / ext4 defaults 0 0

```

contents of mdadm.conf :

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md/0 metadata=1.2 UUID=067051b2:ff104bec:e0744d08:76a99a32 name=rescue:0
ARRAY /dev/md/1 metadata=1.2 UUID=b847912c:37f51b40:db18e3d7:579b580e name=rescue:1
ARRAY /dev/md/2 metadata=1.2 UUID=9a844938:07bf4ec4:73edaa03:c703df5d name=rescue:2

# This configuration was auto-generated on Mon, 25 Aug 2014 15:25:21 +0200
# by mkconf 3.2.5-5
ARRAY /dev/md/1 metadata=1.2 UUID=68e853a6:7af46176:d9c147c7:6ff87bb0 name=company:1

```

Kindly let  me know what I should do. Thanks a lot. :-)

---

### Post by slickymaster on 2015-09-17
*Moved to the ***Server Platforms*** sub-forum*

---

### Post by darkod on 2015-09-17
First small correction. The raid array is not mounted at /dev/md1, the raid array IS the device /dev/md1. HDD and raid arrays device labels like /dev/sdX and /dev/mdX should not be confused with mount points. They are the devices, not mount points. Your /dev/md1 device is mounted at /media/attachment as you can see from the mount output.

Next, take a good look at your mdadm.conf. Apart from the last line which is a definition for /dev/md1, you also have definitions for other three arrays one of which is also called /dev/md1. If these three arrays are no more present, comment those lines by putting # at the start of the lines. Otherwise mdadm will try to assemble them on each boot. In mdadm.conf you should have ARRAY definitions only for arrays that are present, not for old ones.

After you sort that out, you can make the entry in /etc/fstab for /dev/md1. It should be something like:
```
/dev/md1   /media/attachment   ext4   defaults   0   0
```

The mount point /media/attachment is not a very good choice because usually temporary items get mounted in /media. You should consider making new mount point in /mnt or any specific mount point like for example /data, and use that. But of course, changing the mount point now might need you to change many other things in the server configuration. It all depends how /media/attachment is used and by what.

The above should work as a solution to mount the raid at /media/attachment.

---

### Post by akshay-sulakhe on 2015-09-17
Thanks. This helped. I would have to do some considerable changes to make it to /data or something. But with time, I will do it. Thanks a lot. :-)

---

### Post by darkod on 2015-09-17
You're welcome. If you consider your question closed, please mark the thread as Solved. You can do that in Thread Tools above your first post. It helps other people too.

---

