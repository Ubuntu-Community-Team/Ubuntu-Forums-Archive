---
title: "No disk space left despite plenty available"
date: 2017-03-24
forum: Server Platforms
---

### Post by quids on 2017-03-24
My Ubuntu server has run out of disk space on root partition despite having only used 4.5G out of 20G
I have been trying to remove old kernels, but apt is stuck trying to install a new kernel and can't complete as there is no space available.
There is nothing in /tmp, and only a few small config files in /home

The only other folder I could find to delete was an old unused MySQL database, which freed up 160MB, but immediately disappeared.

Any ideas how I can resolve this issue?
Thanks 

```
[FONT=monospace][COLOR=#54FF54]**quids@nas**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ df -h[/COLOR]
Filesystem      Size  Used Avail Use% Mounted on
udev            3.7G     0  3.7G   0% /dev
tmpfs           742M  9.0M  733M   2% /run
/dev/sda2        20G  4.5G     0 100% /
tmpfs           3.7G     0  3.7G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           3.7G     0  3.7G   0% /sys/fs/cgroup
/dev/sda3       212G   32G  179G  15% /mnt/Data
/dev/sda2        20G  4.5G     0 100% /home
/dev/sda1       247M  3.6M  243M   2% /boot/efi
/dev/sdd1       2.7T   63G  2.5T   3% /mnt/Backup
/dev/sdc1       5.5T  3.4T  1.9T  65% /mnt/Drive2 
/dev/sdb1       5.5T  1.7T  3.6T  32% /mnt/Drive1 
tmpfs           742M     0  742M   0% /run/user/1000
[/FONT]
```

```
[FONT=monospace][COLOR=#000000]root@nas:/# apt-get autoremove[/COLOR]
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.  
root@nas:/# 
[/FONT][FONT=monospace][COLOR=#000000]root@nas:/# dpkg --configure -a[/COLOR]
dpkg: error: unable to open/create status database lockfile: No space left on device
[/FONT]
```[FONT=monospace]
[/FONT]
```
[FONT=monospace][COLOR=#54FF54]**quids@nas**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**/var/lib**[/COLOR][COLOR=#000000]$ sudo apt-get install -f[/COLOR]
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libtidy-0.99-0 linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic linux-headers-4.4.0-57
  linux-headers-4.4.0-57-generic linux-headers-4.4.0-59 linux-headers-4.4.0-59-generic
  linux-headers-4.4.0-62 linux-headers-4.4.0-62-generic linux-headers-4.4.0-63
  linux-headers-4.4.0-63-generic linux-image-4.4.0-31-generic linux-image-4.4.0-57-generic
  linux-image-4.4.0-59-generic linux-image-4.4.0-62-generic linux-image-4.4.0-63-generic
  linux-image-extra-4.4.0-31-generic linux-image-extra-4.4.0-57-generic
  linux-image-extra-4.4.0-59-generic linux-image-extra-4.4.0-62-generic
  linux-image-extra-4.4.0-63-generic linux-signed-image-4.4.0-31-generic
  linux-signed-image-4.4.0-57-generic linux-signed-image-4.4.0-59-generic
  linux-signed-image-4.4.0-62-generic linux-signed-image-4.4.0-63-generic python-chardet
  python-feedparser python-libxml2 python-openssl python-utidylib
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-headers-4.4.0-67-generic linux-image-extra-4.4.0-67-generic
The following NEW packages will be installed
  linux-headers-4.4.0-67-generic linux-image-extra-4.4.0-67-generic
0 to upgrade, 2 to newly install, 0 to remove and 48 not to upgrade.
6 not fully installed or removed.
Need to get 36.7 MB of archives.
After this operation, 160 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-headers-4.4.0-67-generic 
amd64 4.4.0-67.88 [779 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-extra-4.4.0-67-gene
ric amd64 4.4.0-67.88 [35.9 MB]
Fetched 36.7 MB in 5s (6,936 kB/s)                              
(Reading database ... 302346 files and directories currently installed.)
Preparing to unpack .../linux-headers-4.4.0-67-generic_4.4.0-67.88_amd64.deb ...
Unpacking linux-headers-4.4.0-67-generic (4.4.0-67.88) ...
dpkg: error processing archive /var/cache/apt/archives/linux-headers-4.4.0-67-generic_4.4.0-67.88_a
md64.deb (--unpack):
 unable to install new version of '/usr/src/linux-headers-4.4.0-67-generic/scripts/basic/.fixdep.cm
d': No space left on device
No apport report written because the error message indicates a disk full error
[/FONT]
```

---

### Post by darkod on 2017-03-24
First, leave apt-get alone. It won't work with 0% free space. It is easy to fix later after you have made free space.

Focus on where the space is because partition of 20GB can't be full by only 4GB.

One confusing thing I see in the df -h results is that sda2 seems to be mounted both as / and /home? Is this true? If you have separate /home you mount it but in such case it is different partition from the /. In your case it seems to be the same. You did this setup?

Second, you have 4 mount point in /mnt. No problem about that except one thing that not many people are aware of: linux mount point is just an empty folder. You mount a partition on it and everything you write into that folder/path is written to that partition instead of inside the root. However if at any time the partition gets unmounted by error, you start writing into the root without even knowing it because the folder path /mnt/folder is inside root. So this way it can easily eat up 16GB on root without you realizing it.

To check that out I would unmount the four partitions you have mounted in /mnt/... and then check the content of those four folders. They should be empty. You might need to stop services like samba to unmount the partitions otherwise they might be locked in use.

Let us know how you get along...

---

### Post by quids on 2017-03-24
I remember having to manually setup the partitioning on the Ubuntu 16.04 server install, but I think I just set it as EFI, /, and a spare partition.
/etc/fstab shows two different lines for / and /home with the same UUID

Anyway, I stopped a load of services and unmounted the drives
```

[COLOR=#54FF54]**quids@nas**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**/mnt**[/COLOR][COLOR=#000000]$ ls -l[/COLOR]
total 0
drwxr-xr-x 1 root  root   0 Dec 20 22:30 [COLOR=#5454FF]**Backup**[/COLOR][COLOR=#000000][/COLOR]
drwxr-xr-x 1 root  root   0 Dec 21 12:12 [COLOR=#5454FF]**cdrom**[/COLOR][COLOR=#000000][/COLOR]
drwxr-xr-x 1 quids quids 40 Dec 20 23:21 [COLOR=#5454FF]**Data**[/COLOR][COLOR=#000000][/COLOR]
drwxr-xr-x 1 root  root   0 Dec 20 22:30 [COLOR=#5454FF]**Drive1**[/COLOR][COLOR=#000000][/COLOR]
drwxr-xr-x 1 root  root   0 Dec 20 22:29 [COLOR=#5454FF]**Drive2**[/COLOR]
[COLOR=#000000][/COLOR]

```
```
[COLOR=#54FF54]**quids@nas**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**/mnt**[/COLOR][COLOR=#000000]$ df -h[/COLOR]
Filesystem      Size  Used Avail Use% Mounted on
udev            3.7G     0  3.7G   0% /dev
tmpfs           742M  9.0M  733M   2% /run
/dev/sda2        20G  4.4G     0 100% /
tmpfs           3.7G     0  3.7G   0% /dev/shm
tmpfs           5.0M     0  5.0M   0% /run/lock
tmpfs           3.7G     0  3.7G   0% /sys/fs/cgroup
/dev/sda2        20G  4.4G     0 100% /home
/dev/sda1       247M  3.6M  243M   2% /boot/efi
tmpfs           742M     0  742M   0% /run/user/1000
```

Still no change. Any other ideas?

---

### Post by quids on 2017-03-24
Ah I think I've just seen it, /mnt/Data is not empty

Edit: It contained only folders, but no files

---

### Post by darkod on 2017-03-24
Become sudo, go to root and check where the space is. Then go into that folder and do the same, etc...
```
sudo -i
cd /
du -sh *
```

Don't forget it might be in hidden files too. The du should show it all in total, but later after you go into a folder there might be hidden files. You can see all files with:
```
ls -alh
```

PS. If you home is within root, there should be no second line for it in fstab. Try commenting that line out. In fact by having it like this you might be doubling up the data (once inside /home and once directly into the partition), but 2x4.5GB is still not 20GB. Unless it got in some weird loop so it is nesting same files over and over...

---

### Post by volkswagner on 2017-03-24
Try using du.

```
sudo su
du -h / --max-depth=1
du -h /home --max-depth=1
```

---

### Post by ian-weisser on 2017-03-25
df -i would be helpful. Out of inodes seems like a possibility to easily prove or disprove.

---

### Post by quids on 2017-03-25
There was a bit more in /home than I thought, but at 119MB thats nothing much.
I tried btrfsck --repair on the SSD, but that didn't make any difference.


```
[FONT=monospace][COLOR=#000000]root@nas:/# du -h / --max-depth=1[/COLOR]
402M    /boot
119M    /home
8.5M    /etc
0       /media
16M     /bin
0       /dev
1.7G    /lib
4.0K    /lib64
0       /mnt
0       /opt
du: cannot access '/proc/3004/task/3004/fd/3': No such file or directory
du: cannot access '/proc/3004/task/3004/fdinfo/3': No such file or directory
du: cannot access '/proc/3004/fd/4': No such file or directory
du: cannot access '/proc/3004/fdinfo/4': No such file or directory
0       /proc
32K     /root
9.1M    /run
14M     /sbin
0       /srv
0       /sys
0       /tmp
1.7G    /usr
287M    /var
0       /snap
4.2G    /
[/FONT]
```

```
[FONT=monospace]root@nas:/# df -i
Filesystem     Inodes IUsed  IFree IUse% Mounted on
udev           943919   599 943320    1% /dev
tmpfs          948886   833 948053    1% /run
/dev/sda2           0     0      0     - /
tmpfs          948886     1 948885    1% /dev/shm
tmpfs          948886     4 948882    1% /run/lock
tmpfs          948886    16 948870    1% /sys/fs/cgroup
/dev/sda2           0     0      0     - /home
/dev/sda1           0     0      0     - /boot/efi
tmpfs          948886     4 948882    1% /run/user/1000
[/FONT]
```[FONT=monospace]
[/FONT]

---

### Post by darkod on 2017-03-25
Are the results the same if you unmount /home? We discussed that sda2 shouldn't be mounted both at / and /home, especially since home folder is inside /.

---

### Post by vasa1 on 2017-03-25
> **quids said:**
> ...
I tried btrfsck ...
Maybe worth mentioning in the first post as well that yours is (or seems to be) a Btrfs filesystem.

BTW, using code tags for terminal output is sufficient. There's usually no need to specify a font or its color unless it's to highlight something out of the ordinary.

---

### Post by quids on 2017-03-25
To be honest I forgot about it being a btrfs file system initially, but yes it my first attempt at using it instead of Ext4.
After searching around a bit more at btrfs results I'm going to try this out: [http://marc.merlins.org/perso/btrfs/post_2014-05-04_Fixing-Btrfs-Filesystem-Full-Problems.html](http://marc.merlins.org/perso/btrfs/post_2014-05-04_Fixing-Btrfs-Filesystem-Full-Problems.html)

I'm pulling more data off the SSD in case I have to flatten it. Once its done I'll drop out to a Live CD and attempt the fix

The colourised font was coming straight from bash and Konsole

```
$ sudo btrfs fi df /
Data, single: total=19.27GiB, used=4.06GiB
System, single: total=4.00MiB, used=16.00KiB
Metadata, single: total=264.00MiB, used=193.48MiB
GlobalReserve, single: total=80.00MiB, used=9.81MiB
$ sudo btrfs fi show /
Label: none  uuid: 3c3f3975-c030-4807-8937-8c848f72ede5
        Total devices 1 FS bytes used 4.25GiB
        devid    1 size 19.53GiB used 19.53GiB path /dev/sda2


```

---

### Post by TheFu on 2017-03-28
If it hasn't been clear, it appears that both / and /home are mounted to the same partition. THIS IS BAD in your setup.  Fix that.

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2        20G  4.5G     0 100% /
/dev/sda2        20G  4.5G     0 100% /home
```
See?  That ain't good.

Fix that first.

---

### Post by quids on 2017-03-30
I ended up flattening my system and rebuilding with Ext4 this time.
The fault with /home and / being on the same partition has also been resolved

---

