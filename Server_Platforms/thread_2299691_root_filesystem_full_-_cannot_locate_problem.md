---
title: "root filesystem full - cannot locate problem"
date: 2015-10-20
forum: Server Platforms
---

### Post by dbecker on 2015-10-20
I'm out of system disk space and I cannot figure out why. 

Here you can see the LV of the root filesystem only has 1.7GB free.

```
root@vernserv5:/# df -h
Filesystem                        Size  Used Avail Use% Mounted on
/dev/mapper/server--vg-root        442G  418G  1.7G 100% /
none                              4.0K     0  4.0K   0% /sys/fs/cgroup
udev                              7.8G   12K  7.8G   1% /dev
tmpfs                             1.6G  2.5M  1.6G   1% /run
none                              5.0M     0  5.0M   0% /run/lock
none                              7.9G     0  7.9G   0% /run/shm
none                              100M     0  100M   0% /run/user
/dev/sda2                         237M   45M  180M  21% /boot
/dev/sdb1                          11T  1.1T  9.3T  10% /data
/dev/sda1                         511M  3.4M  508M   1% /boot/efi
//lanip/admin                     1.4T  955G  421G  70% /media/admin
//lanip/projects                  2.8T  1.6T  1.2T  57% /media/projects
//lanip/ajera                      2.8T  1.6T  1.2T  57% /media/ajera
//lanip/marketing                1.4T  955G  421G  70% /media/marketing
//lanip/archives                  1.4T  955G  421G  70% /media/archives
//lanip/development            1.4T  955G  421G  70% /media/development
//lanip/reference                1.4T  955G  421G  70% /media/reference
//lanip/executive                1.4T  955G  421G  70% /media/executive
//lanip/operations               1.4T  955G  421G  70% /media/operations
//lanip/gis                         5.3T  1.2T  4.1T  22% /media/gis
```

Here I want to list the 20 largest root filesystem directories, excluding /media (other servers mounted here) and /data (the 12TB fileserver array).
If you total these largest 20 directories, you get ~12GB, where are the other 400+ GB? 

```

root@vernserv5:/# du --exclude='*./media/*' --exclude='*./data/*' --exclude='./boot/*' -BM 2>/dev/null | sort -nr | head -n 20
1736M   .
822M    ./usr
478M    ./var
323M    ./usr/share
297M    ./lib
228M    ./var/lib
214M    ./var/cache
188M    ./usr/lib
184M    ./lib/modules/3.13.0-66-generic
184M    ./lib/modules
181M    ./lib/modules/3.13.0-66-generic/kernel
161M    ./var/lib/apt/lists
161M    ./var/lib/apt
146M    ./usr/local/ppbe
146M    ./usr/local
141M    ./usr/share/webmin
138M    ./lib/modules/3.13.0-66-generic/kernel/drivers
112M    ./usr/local/ppbe/jre
111M    ./usr/local/ppbe/jre/lib
108M    ./usr/src
```

I've also tried this command to try and locate large +1GB and +500MB files, nothing was returned. 
```
find . -type f -name "*" -size +1G ! -path "./data/*" ! -path "./media/*" ! -path "./boot/*"
```

Other info: 

ubuntu server 14.04.1
/dev/sdb: 12TB hardware RAID10 array
/dev/sda: 500GB system disk


```

root@vernserv5:/# parted /dev/sda print all
Model: DELL PERC H710 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End    Size   File system  Name  Flags
 1      1049kB  538MB  537MB  fat32              boot
 2      538MB   794MB  256MB  ext2
 3      794MB   500GB  499GB                     lvm


Model: DELL PERC H710 (scsi)
Disk /dev/sdb: 12.0TB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      1049kB  12.0TB  12.0TB  ext4         data


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/server--vg-root: 482GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  482GB  482GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/localbackup--vg-swap_1: 17.1GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  17.1GB  17.1GB  linux-swap(v1)

```

any advice?

thanks.

---

### Post by darkod on 2015-10-20
Hmmm, to avoid any confusion with the command that should ignore /media and /data, why don't you list the full / content and just ignore /media and /data? Does something like this help:
```
cd /
du -sh *
```

That should list all folder size inside /. See if it helps, then you can go level by level to detect exact folder.

---

### Post by dbecker on 2015-10-20
> **darkod said:**
> Hmmm, to avoid any confusion with the command that should ignore /media and /data, why don't you list the full / content and just ignore /media and /data? Does something like this help:
```
cd /
du -sh *
```

That should list all folder size inside /. See if it helps, then you can go level by level to detect exact folder.

That makes sense. Here's the output:

```

root@vernserv5:/# du -sh *
9.7M    bin
47M     boot
1.1T    data
12K     dev
26M     etc
90M     home
0       initrd.img
297M    lib
4.0K    lib64
16K     lost+found
3.3T    media
4.0K    mnt
4.0K    opt
du: cannot access âproc/19355/task/19355/fd/4â: No such file or directory
du: cannot access âproc/19355/task/19355/fdinfo/4â: No such file or directory
du: cannot access âproc/19355/fd/4â: No such file or directory
du: cannot access âproc/19355/fdinfo/4â: No such file or directory
0       proc
128K    root
2.5M    run
12M     sbin
4.0K    srv
0       sys
52K     tmp
822M    usr
478M    var
0       vmlinuz
4.0K    webmin-setup.out

```

As you can see, if we remove:
 /data
/media
/boot

 since they are not part of the root file system quota, then we are left with significantly less than 418G as shown by df -h. 

What's going on here?

---

### Post by steeldriver on 2015-10-20
Sometimes what happens is one of the mounted partitions like /data becomes unmounted, yet a process writes to /data anyway: space gets used on / instead but becomes hidden once /data is re-mounted over the top of it

---

### Post by dbecker on 2015-10-20
interesting, how would I find those hidden files?

/data is our main file server for 10-15 employees, it contains 8 subfolders, each a samba share. 
/media contains 9 subfolders where local shares are mounted, each is used as destination for rsync backup of /data/subfolder shares

Yesterday I noticed all the shares in /media were not mounted. The rsync cronjob runs every night.
As you described above, would rsync have temporarily stored data on the root filesystem inside of /media since the shares were not mounted?

---

### Post by darkod on 2015-10-20
Yes, very weird. And lvdisplay is giving you correct size for the root LV?
```
sudo lvdisplay
```

Have you done recently any size modifications of the LV or the filesystem? But the df -h clearly shows the filesystem size as 442GB. You might also run fsck on the LV but better to be unmounted for that...

---

### Post by darkod on 2015-10-20
Yes, it could. For mounting you have empty folder in / and you mount external device on it. If you unmount the external device (in this case /media) then the media folder remains in / and you can check if it's empty or not.

So in this case with unmount /media the media folder should be empty but it will not be...

---

### Post by dbecker on 2015-10-20
Thanks everyone, that's the problem. 
Unmounted all the external shares from /media and found that all the subfolders are full of data. 

Nice failsafe feature for dummies like me.

Edit: another clue
Have a look at post #3, /media is almost 2x as large as /data
This should have been a clue since /media is backup (mirror) for /data.

---

