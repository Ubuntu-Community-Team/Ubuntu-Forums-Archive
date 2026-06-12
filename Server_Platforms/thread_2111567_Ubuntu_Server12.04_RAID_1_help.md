---
title: "Ubuntu Server12.04 RAID 1 help"
date: 2013-02-02
forum: Server Platforms
---

### Post by no more on 2013-02-02
Hi,

I installed on my old computer Ubuntu Server 12.04 with software RAID 1. Installation was successful, but after a week I decided to check RAID array and I see that one of partition fails to replicate. Please see attached picture.
[IMG]http://prikachi.com/images/897/5814897e.jpg[/IMG]

I read about (sudo mdadm --add/dev/...) but I don't understand how to continue. 
Do I need to reinstall or has another solution?

---

### Post by darkod on 2013-02-02
Can you first post the output of:
```
sudo mdadm --examine /dev/sd[ab]6
```

There should be no need to reinstall. Lets see the --examine details first.

---

### Post by no more on 2013-02-02
Hi, Thanks for the quick response! That is output after:
 "sudo mdadm --examine /dev/sd[ab]6"

[IMG]http://prikachi.com/images/436/5818436d.jpg[/IMG]

---

### Post by darkod on 2013-02-02
You made a mistake, you typed /dev/ds not /dev/sd[ab]6. Try it again.

And there should not be a space before the 6. It's all together /dev/sd[ab]6 without any spaces.

---

### Post by no more on 2013-02-02
That's right. I'm sorry for mistake! Here you are :)

[IMG]http://prikachi.com/images/560/5818560k.jpg[/IMG]

---

### Post by darkod on 2013-02-02
The Events counter of both partitions is very different. I'm not sure if you should try to force assemble the device or not, since /proc/mdstat says sdb6 is active at the moment and sdb6 has much smaller events counter than sda6.

Let me try to ask someone for advice.

---

### Post by rubylaser on 2013-02-02
Can you provide the output of these first?  It would be nice to know what these arrays are doing and how much data is on md2.

```
sudo -i
mount
df -h
```

P.S. You can copy and paste the output from the terminal into code blocks on the forum rather than uploading an image.

---

### Post by no more on 2013-02-02
Hi,
You can see output, but after (sudo -i )nothing happened :

xxx@xxx:~# sudo -i
xxx@xxx:~# mount
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
/dev/md2 on /store type ext4 (rw)
xxx@xxx:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/md0         19G  1.3G   17G   7% /
udev            462M  4.0K  462M   1% /dev
tmpfs           188M  620K  187M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            469M     0  469M   0% /run/shm
/dev/md2         57G  974M   53G   2% /store
xxx@xxx:~#

---

### Post by no more on 2013-02-02
In our local forum advised me to run this .  

code:

sudo mdadm --add /dev/md0 /dev/sda1

---

### Post by no more on 2013-02-02
I did not know that is possible to login like root (sudo -i  :guitar: 

> **no more said:**
> Hi,
You can see output, but after (sudo -i )nothing happened :

xxx@xxx:~# sudo -i
xxx@xxx:~# mount
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
/dev/md2 on /store type ext4 (rw)
xxx@xxx:~# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/md0         19G  1.3G   17G   7% /
udev            462M  4.0K  462M   1% /dev
tmpfs           188M  620K  187M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            469M     0  469M   0% /run/shm
/dev/md2         57G  974M   53G   2% /store
xxx@xxx:~#

---

### Post by darkod on 2013-02-02
> **no more said:**
> In our local forum advised me to run this .  

code:

sudo mdadm --add /dev/md0 /dev/sda1

md0 and md1 seem OK, I wouldn't run any commands on them yet. But they are not mounted anywhere, at least not right now according to the mount and df results.

---

### Post by no more on 2013-02-02
OK. Thanks for provide support friends. I'll reinstall for self training.

---

