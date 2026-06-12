---
title: "df showing incorrect Usage."
date: 2017-04-10
forum: Server Platforms
---

### Post by johnathan3 on 2017-04-10
[COLOR=#111111][FONT=Ubuntu]Someone issued an rsync command to copy files from one disk to another and they messed it up. the commands or something happened on the system where the root / partition became full. they did not exclude some other directories they should have. So I found some files that were in the home directory and deleted them it free'd about 35GB. I cant find where the remaining 150GB is being taken up.
I have rebooted the system a few times and df remains the same.[/FONT][/COLOR]
```
$ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.5 LTS"
NAME="Ubuntu"
VERSION="14.04.5 LTS, Trusty Tahr"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 14.04.5 LTS"
VERSION_ID="14.04"
HOME_URL="http://www.ubuntu.com/"
SUPPORT_URL="http://help.ubuntu.com/"
BUG_REPORT_URL="http://bugs.launchpad.net/ubuntu/"

```

[COLOR=#111111][FONT=Ubuntu]
The rsync command was:[/FONT][/COLOR]
```
sudo rsync -av --progress / /mnt/ssd --exclude /mnt --exclude /proc     --exclude /dev
```
```
$ sudo df -lhaT
Filesystem                   Type         Size  Used Avail Use% Mounted on
sysfs                        sysfs           0     0     0    - /sys
proc                         proc            0     0     0    - /proc
udev                         devtmpfs     1.8G   12K  1.8G   1% /dev
devpts                       devpts          0     0     0    - /dev/pts
tmpfs                        tmpfs        358M  2.5M  355M   1% /run
/dev/sdb1                    ext4         226G  181G   34G  85% /
none                         tmpfs        4.0K     0  4.0K   0% /sys/fs/cgroup
none                         fusectl         0     0     0    - /sys/fs/fuse/connections
none                         debugfs         0     0     0    - /sys/kernel/debug
none                         securityfs      0     0     0    - /sys/kernel/security
none                         tmpfs        5.0M     0  5.0M   0% /run/lock
none                         tmpfs        1.8G   12K  1.8G   1% /run/shm
none                         tmpfs        100M     0  100M   0% /run/user
none                         pstore          0     0     0    - /sys/fs/pstore
binfmt_misc                  binfmt_misc     0     0     0    - /proc/sys/fs/binfmt_misc
systemd                      cgroup          0     0     0    - /sys/fs/cgroup/systemd
/home/cata/.Private          ecryptfs     226G  181G   34G  85% /home/cata
```

```
$  sudo lsof | grep deleted
```
```

$ pwd
/
```
```
$ sudo du -hsc
du: cannot access &#8216;./proc/22085/task/22085/fd/4&#8217;: No such file or directory
du: cannot access &#8216;./proc/22085/task/22085/fdinfo/4&#8217;: No such file or directory
du: cannot access &#8216;./proc/22085/fd/4&#8217;: No such file or directory
du: cannot access &#8216;./proc/22085/fdinfo/4&#8217;: No such file or directory
6.4G    .
6.4G    total
cata@server1:/$
```

```
$ cd /home/cata/
$ sudo du -hsc
516K    .
516K    total
```
[COLOR=#111111][FONT=Ubuntu]I installed ncdu and it does not show this space used.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I need to free up this space for some additional data being generated in a few days.[/FONT][/COLOR]

---

### Post by darkod on 2017-04-10
Check the free inodes with:
```
df -i
```

In case you have no free inodes left, that is your issue probably. There seems to be some more info here: [https://www.ivankuznetsov.com/2010/02/no-space-left-on-device-running-out-of-inodes.html](https://www.ivankuznetsov.com/2010/02/no-space-left-on-device-running-out-of-inodes.html)

Also, I see you have encrypted home (or part of it). Does the user you are using to check the free space have permissions to look inside this encrypted folder? Otherwise it might be simply ignoring the data size inside.

---

### Post by johnathan3 on 2017-04-10
yes the encrypted home is for the user issuing the commands.

```
$ sudo df -i
[sudo] password for cata:
Filesystem                     Inodes      IUsed     IFree    IUse% Mounted on
udev                           453824        552      453272    1%     /dev
tmpfs                          457299        545      456754    1%     /run
/dev/sdb1                    15032320     218773         14813547 2%     /
none                           457299          2       457297    1%     /sys/fs/cgroup
none                           457299          2       457297    1%     /run/lock
none                           457299          2       457297    1%     /run/shm
none                           457299          2       457297    1%     /run/user
/home/cata/.Private              15032320   218773   14813547 2%     /home/cata

```

---

### Post by darkod on 2017-04-10
I have LVM so I can't really compare the df results when using encrypted home. Was that /home/cata always like that in the df results?

I find it strange to see /home/cata mounted at /home/cata. Usually you mounted partitions or logical volumes.

I would also try this:
1. Go into /home/cata and run:
```
du -sh *
```

2. Go into /home/cata/.Private and do the same.

See if that helps you find folders with huge data in it.

---

### Post by johnathan3 on 2017-04-10
```
$ sudo du -sh /home/cata/
532K    /home/cata/
$ sudo du -sh /home/cata/.Private
4.0K    /home/cata/.Private

```


Nothing I can see in there.

---

### Post by darkod on 2017-04-11
Unfortunately nothing I can see too. I would try unmounting the /home/cata, just to make sure it is not creating any confusion, because for me personally it does.

I would switch to root with sudo -i, and then umount /home/cata.

Then try to look at the root partition again with something like:
```
cd /
du -sh *
```

See if that gives you more clues... You never replied to my questions if the system mount points were always like that. Because I find it strange to have /home/cata mounted on /home/cata (like nested inside itself). I think that situation can provoke weird results of free space calculation.

---

### Post by johnathan3 on 2017-04-11
If I unmount /home/cata it is the same. because it is an encrypted homefolder is why .Private is mounted to /home/cata


sudo du -hsc
du: cannot access &#8216;./proc/22085/task/22085/fd/4&#8217;: No such file or directory
du: cannot access &#8216;./proc/22085/task/22085/fdinfo/4&#8217;: No such file or directory
du: cannot access &#8216;./proc/22085/fd/4&#8217;: No such file or directory
du: cannot access &#8216;./proc/22085/fdinfo/4&#8217;: No such file or directory
6.4G    .
6.4G    total
cata@server1:/$

---

### Post by darkod on 2017-04-11
Aren't you missing the * to tell it to browse all folders? There should be many inside /, all system folders are there (etc, var, mnt...). How about trying literary (don't leave out anything):
```
du -sh *
```

I am not sure how encrypted foders mount, but I would still not use folder from inside the mount point for that same mount point. Unless that is by design in ubuntu. On my desktop I have encrypted home and data LV and the mount points look to me like what I would expect:
```
/dev/mapper/crhome    36G   29G  5.2G  85% /home
/dev/mapper/crdata    50G   35G   13G  75% /data
```

---

### Post by johnathan3 on 2017-04-11
If I unmount /home/cata it is the same. because it is an encrypted homefolder is why .Private is mounted to /home/cata


sudo du -hsc
du: cannot access &#8216;./proc/22085/task/22085/fd/4&#8217;: No such file or directory
du: cannot access &#8216;./proc/22085/task/22085/fdinfo/4&#8217;: No such file or directory
du: cannot access &#8216;./proc/22085/fd/4&#8217;: No such file or directory
du: cannot access &#8216;./proc/22085/fdinfo/4&#8217;: No such file or directory
6.4G    .
6.4G    total
cata@server1:/$

---

### Post by johnathan3 on 2017-04-11
Figured it out.

I guess at some point /proc was double mounted and created a new /proc/.kcore file

I did
```

sudo umount -a

```

which umounted /proc

and revealed another /proc underneath which had a 170GB kcore file. I deleted that file. and my space came back.

```

/proc$ ls -lthra
dr-xr-xr-x 151 root root 4.0K Apr  8 23:49 .
dr-xr-xr-x   9 root root 4.0K Apr  8 23:49 1028
dr-xr-xr-x   9 root root 4.0K Apr  8 23:49 10
-rw-------   1 root root 174G Apr  9 01:04 .kcore.R4Thaa
dr-x------   2 root root 4.0K Apr 11 16:13 3397
drwxr-xr-x  24 root root 4.0K Apr 11 16:19 ..
/proc$ sudo rm -rf .kcore.R4Thaa

```

Had to physically reboot the machine since reboots from command no longer work after unmounting /proc

Now my space is back:

```

$ df -hT
Filesystem                   Type      Size  Used Avail Use% Mounted on
udev                         devtmpfs  1.8G  4.0K  1.8G   1% /dev
tmpfs                        tmpfs     358M  928K  357M   1% /run
/dev/sdb1                    ext4      226G  6.4G  208G   3% /
none                         tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
none                         tmpfs     5.0M  4.0K  5.0M   1% /run/lock
none                         tmpfs     1.8G  8.0K  1.8G   1% /run/shm
none                         tmpfs     100M     0  100M   0% /run/user
/home/cata/.Private ecryptfs  226G  6.4G  208G   3% /home/cata
/dev/mapper/Enc5             ext4      7.3T  5.7T  1.3T  83% /NAS

```

---

