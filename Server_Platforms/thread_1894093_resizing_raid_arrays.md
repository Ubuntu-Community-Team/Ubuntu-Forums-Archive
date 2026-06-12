---
title: "resizing raid arrays"
date: 2011-12-11
forum: Server Platforms
---

### Post by brighty22 on 2011-12-11
Hi,

I've just tried a dist-upgrade on my home server and from the errors found that the /boot partition is completely full. These are the raid arrays on the server:

```
george@bright2a:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md2 : active raid5 sdb3[1] sda3[0] sdd3[3] sdc3[2]
      4394236416 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]

md0 : active raid1 sdb1[1] sda1[0] sdc1[2] sdd1[3]
      96244 blocks super 1.2 [4/4] [UUUU]

md1 : active raid5 sda2[0] sdb2[1] sdd2[3] sdc2[2]
      877056 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]

unused devices: <none>
```

Is there any way of reducing the size of md2 (my main raid5 storage array) by several hundred MB and giving the freed up space to md0 (the raid1 /boot array), using mdadm or some other tool?

Thanks for any help!

---

### Post by rubylaser on 2011-12-12
You can resize the filesystems, then the partitions for the arrays, but have you tried to clean up old kernels and kernel headers in your /boot partition first?

How large is your /boot partition?

---

### Post by brighty22 on 2011-12-12
Thanks for your reply. I've done apt-get autoremove. It's 100MB; du is saying 82MB is used.

---

### Post by rubylaser on 2011-12-12
100MB is small but should be sufficient.  Autoremove will not remove old kernels and headers. Have you actually looked in /boot to verify what's there?  Here's a du -h on 2 of my Lucid servers at work...

```
root@svr-cc-web:/boot# du -h --max-depth=1
4.3M	./grub
20M	.

root@svr-cc-marketing:~# du -h --max-depth=1
8.0K	./.ssh
4.0K	./Mail
4.0K	./.aptitude
48K	./.subversion
4.0K	./.debtags
4.0K	./.cache
20M	./nipper-ng-read-only
12K	./scripts
4.0K	./test
25M	.
```

Here's an example of what I mean. This server has not been cleaned up **(93MB)**.
```
root@svr-cc-mysql:/boot# du -h --max-depth=1
4.3M	./grub
93M	.
```

```
root@svr-cc-mysql:/boot# ls
abi-2.6.32-24-server         memtest86+.bin
abi-2.6.32-26-server         System.map-2.6.32-24-server
abi-2.6.32-27-server         System.map-2.6.32-26-server
abi-2.6.32-28-server         System.map-2.6.32-27-server
abi-2.6.32-29-server         System.map-2.6.32-28-server
abi-2.6.32-30-server         System.map-2.6.32-29-server
config-2.6.32-24-server      System.map-2.6.32-30-server
config-2.6.32-26-server      vmcoreinfo-2.6.32-24-server
config-2.6.32-27-server      vmcoreinfo-2.6.32-26-server
config-2.6.32-28-server      vmcoreinfo-2.6.32-27-server
config-2.6.32-29-server      vmcoreinfo-2.6.32-28-server
config-2.6.32-30-server      vmcoreinfo-2.6.32-29-server
grub                         vmcoreinfo-2.6.32-30-server
initrd.img-2.6.32-24-server  vmlinuz-2.6.32-24-server
initrd.img-2.6.32-26-server  vmlinuz-2.6.32-26-server
initrd.img-2.6.32-27-server  vmlinuz-2.6.32-27-server
initrd.img-2.6.32-28-server  vmlinuz-2.6.32-28-server
initrd.img-2.6.32-29-server  vmlinuz-2.6.32-29-server
initrd.img-2.6.32-30-server  vmlinuz-2.6.32-30-server
```

As you can see autoremove doesn't remove anything.
```
root@svr-cc-mysql:/boot# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 128 not upgraded.
```

Here's a command that will clean up all of your old kernels and headers for you.
```
sudo -i
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
```

This will clean up all but your current running kernel.

After cleaning up...
```

root@svr-cc-mysql:/boot# ls -la
total 15208
drwxr-xr-x  3 root root    4096 2011-12-12 10:59 .
drwxr-xr-x 23 root root    4096 2011-12-12 10:59 ..
-rw-r--r--  1 root root  646419 2011-03-01 21:02 abi-2.6.32-30-server
-rw-r--r--  1 root root  110687 2011-03-01 21:02 config-2.6.32-30-server
drwxr-xr-x  3 root root    4096 2011-12-12 10:59 grub
-rw-r--r--  1 root root 8331342 2011-03-18 06:54 initrd.img-2.6.32-30-server
-rw-r--r--  1 root root  160280 2010-03-23 05:40 memtest86+.bin
-rw-r--r--  1 root root 2179117 2011-03-01 21:02 System.map-2.6.32-30-server
-rw-r--r--  1 root root    1336 2011-03-01 21:08 vmcoreinfo-2.6.32-30-server
-rw-r--r--  1 root root 4111552 2011-03-01 21:02 vmlinuz-2.6.32-30-server

```
and the space saved...
```
root@svr-cc-mysql:/boot# du -h --max-depth=1
4.3M	 ./grub
20M	 .
```

Back to 20M again :)  Hopefully, you can run that command and get your /boot back down to proper size.  If that doesn't work, then please read on.

I'm assuming md0 is a RAID1.  From the livecd, you could copy the contents of /boot to back it up.  Then, you could convert the RAID1 to a RAID10 array, something like [this]("http://serverfault.com/questions/43677/best-way-to-grow-linux-software-raid-1-to-raid-10") should work.  Finally, grow the filesystem to take advantage of the new space.

---

### Post by brighty22 on 2011-12-12
Thanks again. You're right; this is my /boot:

```
george@bright2a:/boot$ sudo du -h --max-depth=1
1.5M    ./grub
12K     ./lost+found
82M     .
```

```
george@bright2a:/boot$ ls
abi-2.6.38-10-generic-pae         memtest86+.bin
abi-2.6.38-11-generic-pae         memtest86+_multiboot.bin
abi-2.6.38-12-generic-pae         System.map-2.6.38-10-generic-pae
abi-2.6.38-8-generic-pae          System.map-2.6.38-11-generic-pae
config-2.6.38-10-generic-pae      System.map-2.6.38-12-generic-pae
config-2.6.38-11-generic-pae      System.map-2.6.38-8-generic-pae
config-2.6.38-12-generic-pae      vmcoreinfo-2.6.38-10-generic-pae
config-2.6.38-8-generic-pae       vmcoreinfo-2.6.38-11-generic-pae
grub                              vmcoreinfo-2.6.38-12-generic-pae
initrd.img-2.6.38-10-generic-pae  vmcoreinfo-2.6.38-8-generic-pae
initrd.img-2.6.38-11-generic-pae  vmlinuz-2.6.38-10-generic-pae
initrd.img-2.6.38-12-generic-pae  vmlinuz-2.6.38-11-generic-pae
initrd.img-2.6.38-8-generic-pae   vmlinuz-2.6.38-12-generic-pae
lost+found                        vmlinuz-2.6.38-8-generic-pae
```

However when I run your command, I get the following:

```
root@bright2a:~# dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r |                                 cut -f1,2 -d"-"` | grep -e [0-9] | xargs sudo apt-get -y purge
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-generic-pae : Depends: linux-image-2.6.38-13-generic-pae but it is not                                 going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solu                                tion).
```

When I ran apt-get -f install, this happened:

```
root@bright2a:~# apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-12-generic-pae linux-headers-2.6.38-12
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-2.6.38-13-generic-pae
Suggested packages:
  fdutils linux-doc-2.6.38 linux-source-2.6.38 linux-tools
The following NEW packages will be installed
  linux-image-2.6.38-13-generic-pae
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
Need to get 0 B/36.0 MB of archives.
After this operation, 114 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 113386 files and directories currently installed.)
Unpacking linux-image-2.6.38-13-generic-pae (from .../linux-image-2.6.38-13-generic-pae_2.6.38-13.52_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.38-13-generic-pae_2.6.38-13.52_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-2.6.38-13-generic-pae': No space left on device
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.38-13-generic-pae /boot/vmlinuz-2.6.38-13-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.38-13-generic-pae /boot/vmlinuz-2.6.38-13-generic-pae
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.38-13-generic-pae_2.6.38-13.52_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Help!!

---

### Post by rubylaser on 2011-12-12
Looks like you've got the package manager in a fun state :) Run and apt-get update, then try apt-get -f install again. What's the output of
```
uname -r
```

---

### Post by brighty22 on 2011-12-12
Failed again with the same errors...

```
george@bright2a:~$ uname -r
2.6.38-12-generic-pae
```

---

### Post by rubylaser on 2011-12-12
try running an apt-get dist-upgrade and see if that clears it up.

---

### Post by brighty22 on 2011-12-12
Nope. Running out of space has really messed up the package manager... might just go for a clean install.

---

### Post by rubylaser on 2011-12-12
Yuck, that doesn't sound too appealing :) Have you tried to remove some of the old packages by hand?
```
apt-get remove  --purge linux-image-2.6.38-8-generic-pae
```

And tried to install by hand the package it's missing after removing some of those.

```
linux-image-2.6.38-13-generic-pae
```

---

### Post by brighty22 on 2011-12-12
Yep.. everything to do with apt-get seems to come back to 'E: Unmet dependencies.'... even when using -f.

```
george@bright2a:~$ sudo apt-get remove --purge linux-image-2.6.38-8-generic-pae
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-image-generic-pae : Depends: linux-image-2.6.38-13-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by rubylaser on 2011-12-12
Give it a try with aptitude, it's better at resolving unmet dependencies.
```
sudo aptitude remove linux-image-2.6.38-8-generic-pae
```

---

### Post by brighty22 on 2011-12-12
```
george@bright2a:/boot$ sudo du -h --max-depth=1
1.5M    ./grub
12K     ./lost+found
22M     .
```

You're a genius :D

---

### Post by rubylaser on 2011-12-12
Thanks for the compliment :)  I'm glad you got it sorted out.  Please mark the thread as solved under the thread tools at the top.

---

