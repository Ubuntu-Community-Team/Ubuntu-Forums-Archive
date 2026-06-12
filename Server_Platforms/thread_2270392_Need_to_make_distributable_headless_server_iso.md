---
title: "Need to make distributable headless server iso"
date: 2015-03-22
forum: Server Platforms
---

### Post by bizres on 2015-03-22
Hello,

I've built a headless server based out of the Ubuntu minimal server edition 14.04 and added things like web based medical apps, magento, and scripts to integrate.

I want to now make this distributable.

Not sure how I can go about doing this.
I've been looking at remastersys and the likes,but they all seem to be working around GUI while my server is a headless machine.

Is there a way to make remasterys (or any alternative) work around this?

Thanks in anticipation.

---

### Post by sudodus on 2015-03-22
Please describe the partitioning of the server system, post the output of the following commands

```
sudo parted -l
df -h
```

and I can tell, if there is some simple method for you.

---

### Post by bizres on 2015-03-25
> **sudodus said:**
> ```
sudo parted -l
df -h
```

Thanks Sudodus

```
$ sudo parted -l
[sudo] password for openemr:
Model: ATA VBOX HARDDISK (scsi)
Disk /dev/sda: 8590MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  7516MB  7515MB  primary   ext4            boot
 2      7517MB  8589MB  1072MB  extended
 5      7517MB  8589MB  1072MB  logical   linux-swap(v1)
```


```
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       6.8G  1.9G  4.6G  29% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            492M  4.0K  492M   1% /dev
tmpfs           101M  432K  100M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            501M     0  501M   0% /run/shm
none            100M     0  100M   0% /run/user
```

---

### Post by sudodus on 2015-03-25
You have a simple system with [only] a root partition **/dev/sda1** and a swap partition **/dev/sd5**

Then you can use the ***One Button Installer*** to make a ***tarball*** of your installed headless server. After that you can use the One Button Installer to install copies of the headless server into other computers.

See these links

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

[This is a link to a detailed description how to make your own tarball]("https://help.ubuntu.com/community/OBI/MakeOBItarball")

---

