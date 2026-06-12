---
title: "Resize LVM virtual partition on Disco Dingo server"
date: 2019-10-06
forum: Server Platforms
---

### Post by sijpkes on 2019-10-06
Hi there, I've setup a media server using the default LVM settings on Ubuntu Server. I'm not sure if this was the best setting to use, but this is my first time setting up this sort of thing.

Unfortunately, the root / partition has run out of space already. I'd like to remove the udev partition to free up the root but I don't know how to safely do this. 

Here is my setup:

```
udev                              devtmpfs  1.9G     0  1.9G   0% /dev
tmpfs                             tmpfs     383M  1.2M  381M   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv ext4      3.9G  3.7G     0 100% /
tmpfs                             tmpfs     1.9G     0  1.9G   0% /dev/shm
tmpfs                             tmpfs     5.0M     0  5.0M   0% /run/lock
tmpfs                             tmpfs     1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/sda2                         ext4      976M   84M  826M  10% /boot
/dev/loop2                        squashfs   43M   43M     0 100% /snap/gtk-common-themes/1313
/dev/loop4                        squashfs   55M   55M     0 100% /snap/lxd/11985
/dev/loop0                        squashfs   90M   90M     0 100% /snap/core/6673
/dev/loop6                        squashfs   27M   27M     0 100% /snap/heroku/3826
/dev/loop5                        squashfs   90M   90M     0 100% /snap/core/7713
/dev/loop10                       squashfs   55M   55M     0 100% /snap/core18/1192
/dev/loop3                        squashfs  218M  218M     0 100% /snap/wine-platform-runtime/37
/dev/loop7                        squashfs   74M   74M     0 100% /snap/wine-platform-3-stable/6
/dev/sdb2                         fuseblk   3.7T  555G  3.1T  15% /media/movies
/dev/loop11                       squashfs   55M   55M     0 100% /snap/core18/1144
/dev/loop9                        squashfs   27M   27M     0 100% /snap/heroku/3822
/dev/loop8                        squashfs   98M   98M     0 100% /snap/docker/384
/dev/loop1                        squashfs   54M   54M     0 100% /snap/lxd/10601
/dev/sda1                         vfat      511M  7.6M  504M   2% /boot/efi
tmpfs                             tmpfs     383M     0  383M   0% /run/user/1000
/dev/sdd                          fuseblk   299G   11M  299G   1% /media/workspace

```

All help is greatly appreciated.

---

### Post by LHammonds on 2019-10-06
I cringe at using the default "EVERYTHING IN ONE PARTITION" option.  I know many like the simplicity but you are experiencing the exact reason for avoiding it...filling up root...which causes the OS to freak out.

So anything other than files in /boot is going to affect the root partition (because it is all on one) so find the files you have been adding which filled it up and remove those 1st.

After you have enough space for the OS to work, you might want to consider adding additional space...but I would only do that AFTER I re-install the entire system and separate the partitions during install which will allow you to allocate space where you need it and prevent applications or data from filling up root.  I explain how to do this in this thread here: [How to install Ubuntu server 18.04 LTS](https://hammondslegacy.com/forum/viewtopic.php?f=40&t=244)

LHammonds

---

### Post by sijpkes on 2019-10-06
Thanks @LHammonds, yes I had setup a Linux Mint box about 10 years ago, but I'd forgotten this important detail of the setup! 

So there is no way that you can re-assign the space allocated to udev to /dev/mapper/ubuntu--vg-ubuntu--lv?

I read somewhere that LVMs were easier to resize, but I don't fully understand the concept.

---

### Post by Dennis N on 2019-10-06
The logical volume for your root file system is very small.
```
/dev/mapper/ubuntu--vg-ubuntu--lv ext4      3.9G  3.7G     0 100% /
```
See if there is room in it's volume group to enlarge it. Post output of:
```
sudo vgs
```

---

### Post by TheFu on 2019-10-06
First, let's clean up the cruft and reorder the the output:
```
/dev/mapper/ubuntu--vg-ubuntu--lv ext4      3.9G  3.7G     0 100% /
/dev/sda1                         vfat      511M  7.6M  504M   2% /boot/efi 
/dev/sda2                         ext4      976M   84M  826M  10% /boot 
/dev/sdb2                         fuseblk   3.7T  555G  3.1T  15% /media/movies 
/dev/sdd                          fuseblk   299G   11M  299G   1% /media/workspace
```

Keeping the output simple makes it easier to help and reduces possible confusion.
**df -hT -x squashfs -x tmpfs -x devtmpfs** should make for cleaner output. It is so useful, I made an alias for that, dft.

The output from 
```
lsblk -o name,size,type,fstype,mountpoint
``` would be helpful. Another alias, lsbt. Just too useful. Got this one from an expert in these forums.  Also, whenever dealing with LVM, seeing the output from **pvs, vgs, lvs** is helpful.

Clearly, 3.9GB is way, way, too small for /.  15G is a reasonable minimal, but 25G would provide extra room for most people provided they aren't running servers.  If you run a server, like plex, then it is smart to place /var/ into a separate LV.  My plex server /var/lib/plexmediaserver/ is about 65G in size holding all the metadata for the media which is stored on other disks.


I have no complaints about either the /boot or /boot/efi partition sizes. 
I do have a complaint about sdd not using a partition table.  This is dangerous since most file/partitioning tools expect a partition table and will freak out if there isn't one, like you've done there.  Also, is that NTFS?  That's a less good choice. 

If you post the output requested, then we can show how easy it is to address this, but not without seeing how large the VG is and how much total space is available.

---

### Post by TheFu on 2019-10-06
And just to be quick if this is all you want to know, making about 50 assumptions about the system which might not be true ... 
```
sudo lvresize -L +20G -r /dev/mapper/ubuntu--vg-ubuntu--lv
```
will add 20G and resize up the file system for the LV.  It will take about 3 seconds and can be performed while the system is being used.  Growing is easy, but really it would make sense to not grow / larger than 25G.

Use other LVs for other places.  I would definitely create a new LV just for /var/ due to plex needs.

---

### Post by sijpkes on 2019-10-06
Thanks@Thefu and @Dennis N, for some reason my default install had only taken up 4gb of a 250gb hard drive. I've ended up using lvm to resize it to the remaining space.

```

****:~$ sudo lvm
lvm> lvextend -l +100%FREE /dev/ubuntu-vg/ubuntu-lv
  Size of logical volume ubuntu-vg/ubuntu-lv changed from 4.00 GiB (1024 extents) to 231.38 GiB (59234 extents).
  Logical volume ubuntu-vg/ubuntu-lv successfully resized.
lvm> exit
  Exiting.
****:~$ sudo resize2fs /dev/ubuntu-vg/ubuntu-lv
resize2fs 1.44.6 (5-Mar-2019)
Filesystem at /dev/ubuntu-vg/ubuntu-lv is mounted on /; on-line resizing required
old_desc_blocks = 1, new_desc_blocks = 29
The filesystem on /dev/ubuntu-vg/ubuntu-lv is now 60655616 (4k) blocks long.

****:~$ df -h

```

---

### Post by TheFu on 2019-10-07
Really wish you would have used my command.  It resized to a specific size and would have handled the file system extension in 1 command.  Whatever.

Having / over 25G will make all sorts of other issues for your system.

There are REASONS why we make specific suggestions.

Oh, well.  You'll learn about those on your own.  Hopefully, it will not cost total data loss for that lesson.

---

