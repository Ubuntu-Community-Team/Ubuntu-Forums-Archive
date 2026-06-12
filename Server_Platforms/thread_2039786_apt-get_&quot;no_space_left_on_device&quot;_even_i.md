---
title: "apt-get &quot;no space left on device&quot; even it is %97 free"
date: 2012-08-09
forum: Server Platforms
---

### Post by vhtmg108 on 2012-08-09
Hi Guys,

I have a problem which makes me go grazy for 3 days.

On a newly installed Ubuntu server 12.04, I setup lxde and firefox via apt-get.

While I was trying to setup virtual-box I started to get "no space left on device" errors. Depending on the first failure, the linux-headers were broken. Now I cannot setup anything.

```
**apt-get install thunderbird**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-headers-generic : Depends: linux-headers-3.2.0-27-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

When I try to run "apt-get -f install" to fix linux-headers, I get "no space left on device" error.
```
**apt-get -f install**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  java-common tzdata-java
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.2.0-27 linux-headers-3.2.0-27-generic
The following NEW packages will be installed:
  linux-headers-3.2.0-27 linux-headers-3.2.0-27-generic
0 upgraded, 2 newly installed, 0 to remove and 71 not upgraded.
1 not fully installed or removed.
Need to get 12.7 MB of archives.
After this operation, 67.4 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-27 all 3.2.0-27.43 [11.7 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-27-generic amd64 3.2.0-27.43 [987 kB]                                              
Fetched 12.7 MB in 27s (454 kB/s)                                                                                                                                      
(Reading database ... 45846 files and directories currently installed.)
Unpacking linux-headers-3.2.0-27 (from .../linux-headers-3.2.0-27_3.2.0-27.43_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-27_3.2.0-27.43_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-27/arch/mips/include/asm/xtalk/xwidget.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-27/arch/mips/include/asm/xtalk/xwidget.h'):
**No space left on device**
**No apport report written because the error message indicates a disk full error**
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Unpacking linux-headers-3.2.0-27-generic (from .../linux-headers-3.2.0-27-generic_3.2.0-27.43_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-27-generic_3.2.0-27.43_amd64.deb (--unpack):
 error creating symbolic link `./usr/src/linux-headers-3.2.0-27-generic/include/linux/writeback.h': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-27_3.2.0-27.43_all.deb
 /var/cache/apt/archives/linux-headers-3.2.0-27-generic_3.2.0-27.43_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The disk is totally empty.
```

**df -Th**
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sdb1      ext4       68G  1.9G   62G   3% /
udev           devtmpfs  2.0G  4.0K  2.0G   1% /dev
tmpfs          tmpfs     791M  412K  791M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     2.0G   68K  2.0G   1% /run/shm
```


Please give some advice. You can see the df result and the error.

Thanks.

---

### Post by vhtmg108 on 2012-08-09
By the way here you see iNode allocation.

```
[B]df -i
[/B]Filesystem     Inodes IUsed  IFree IUse% Mounted on
/dev/sdb1       68736 61280   7456   90% /
udev           503875   535 503340    1% /dev
tmpfs          506069   406 505663    1% /run
none           506069     3 506066    1% /run/lock
none           506069     2 506067    1% /run/shm
```

---

### Post by koenn on 2012-08-09
while 90% inode usages suggest you still have some left, it's sufficiently high that I'd consider it the cause of the 'disk full' error. 

YOu do that by deleting files; high inode usage with lots of disk space left suggests you have an insane large amount of very small files somewhere

Here are some people who ecperienced the same, and their fixes:

[http://stackoverflow.com/questions/653096/howto-free-inode-usage](http://stackoverflow.com/questions/653096/howto-free-inode-usage)
[http://www.nzlinux.com/2010/06/inode-problems-and-full-disks/](http://www.nzlinux.com/2010/06/inode-problems-and-full-disks/)
[http://paulscomputernotes.blogspot.be/2012/06/disk-full-but-still-space-available.html](http://paulscomputernotes.blogspot.be/2012/06/disk-full-but-still-space-available.html)

---

### Post by shawn.sustaita on 2013-05-28
I'm having the same issue but I'm using a filesystem (btrfs) that dynamically allocates inodes, according to the following site.

[https://btrfs.wiki.kernel.org/index.php/Main_Page](https://btrfs.wiki.kernel.org/index.php/Main_Page)

I'm a newbie to btrfs.  Speaking of newbie, I believe this is my first post to this forum.

Here's my disk information:

 root@shawnito:~# df -hT
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda3      btrfs      28G   16G   12G  57% /
udev           devtmpfs  1.9G  4.0K  1.9G   1% /dev
tmpfs          tmpfs     769M  856K  768M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     1.9G  2.7M  1.9G   1% /run/shm
/dev/sda2      ext4      462M  126M  313M  29% /boot
/dev/sda3      btrfs      28G   16G   12G  57% /home
/dev/sda1      vfat       95M  120K   95M   1% /boot/efi

root@shawnito:~# df -hTi
Filesystem     Type     Inodes IUsed IFree IUse% Mounted on
/dev/sda3      btrfs         0     0     0     - /
udev           devtmpfs   479K   562  478K    1% /dev
tmpfs          tmpfs      481K   504  480K    1% /run
none           tmpfs      481K     4  481K    1% /run/lock
none           tmpfs      481K    11  481K    1% /run/shm
/dev/sda2      ext4       120K   235  120K    1% /boot
/dev/sda3      btrfs         0     0     0     - /home
/dev/sda1      vfat          0     0     0     - /boot/efi

Thoughts?

---

### Post by shawn.sustaita on 2013-05-28
I've tried numerous techniques to fix the issue but none have worked.

Here's the obvious choice:

root@shawnito:/boot# apt-get -f install
Reading package lists... Done
Building dependency tree * * **
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
* linux-headers-3.2.0-44
The following NEW packages will be installed:
* linux-headers-3.2.0-44
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
3 not fully installed or removed.
Need to get 0 B/11.7 MB of archives.
After this operation, 56.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 566190 files and directories currently installed.)
Unpacking linux-headers-3.2.0-44 (from .../linux-headers-3.2.0-44_3.2.0-44.69_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-44_3.2.0-44.69_all.deb (--unpack):
*unable to install new version of `./usr/src/linux-headers-3.2.0-44/arch/arm/mach-sa1100/include/mach': No space left on device
No apport report written because the error message indicates a disk full error
* * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * * dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
*/var/cache/apt/archives/linux-headers-3.2.0-44_3.2.0-44.69_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@shawnito:/boot#

---

### Post by shawn.sustaita on 2013-05-28
Indeed, it was a space issue; although, it wasn't apparent from my df commands.  Apparently, I need to learn more about btrfs.

---

