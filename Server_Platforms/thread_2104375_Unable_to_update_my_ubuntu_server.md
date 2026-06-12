---
title: "Unable to update my ubuntu server"
date: 2013-01-12
forum: Server Platforms
---

### Post by Futureking on 2013-01-12
When I try to update my ubuntu server 12.04 I get the following error:

You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-generic-pae : Depends: linux-image-3.2.0-34-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

.. install failed!

But When I run apt-get -f install 
I get following error:
[http://postimage.org/image/aiuo1cq8r/](http://postimage.org/image/aiuo1cq8r/)

[IMG]http://s9.postimage.org/ymlfpn8pr/ubuntu_error.jpg[/IMG]

---

### Post by Doug S on 2013-01-12
Is your /boot drive full? You might need to remove some older kernels. Example:```
doug@s15:~$ [COLOR=red]df[/COLOR]
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/s15-root 952975268 467367364 437199536  52% /
udev                   7993260         8   7993252   1% /dev
tmpfs                  3200936       756   3200180   1% /run
none                      5120         0      5120   0% /run/lock
none                   8002336         0   8002336   0% /run/shm
cgroup                 8002336         0   8002336   0% /sys/fs/cgroup
/dev/sda1               233191    189216     31534  [COLOR=red]86%[/COLOR] /boot  [COLOR=red]<<< Oh, getting full[/COLOR]
doug@s15:~$ [COLOR=red]ls -l /boot[/COLOR]
total 185156
-rw-r--r-- 1 root root   791281 Jul  6  2012 abi-3.2.0-27-generic
-rw-r--r-- 1 root root   791281 Jul 27 10:44 abi-3.2.0-29-generic
-rw-r--r-- 1 root root   791446 Aug 24 10:33 abi-3.2.0-30-generic
-rw-r--r-- 1 root root   791446 Sep  7 09:57 abi-3.2.0-31-generic
-rw-r--r-- 1 root root   792532 Sep 26 15:14 abi-3.2.0-32-generic
-rw-r--r-- 1 root root   792532 Oct 18 10:10 abi-3.2.0-33-generic
-rw-r--r-- 1 root root   792587 Nov 15 03:29 abi-3.2.0-34-generic
-rw-r--r-- 1 root root   792715 Dec  5 10:22 abi-3.2.0-35-generic
-rw-r--r-- 1 root root   140454 Jul  6  2012 config-3.2.0-27-generic
-rw-r--r-- 1 root root   140432 Jul 27 10:44 config-3.2.0-29-generic
-rw-r--r-- 1 root root   140432 Aug 24 10:33 config-3.2.0-30-generic
-rw-r--r-- 1 root root   140459 Sep  7 09:57 config-3.2.0-31-generic
-rw-r--r-- 1 root root   140488 Sep 26 15:14 config-3.2.0-32-generic
-rw-r--r-- 1 root root   140488 Oct 18 10:10 config-3.2.0-33-generic
-rw-r--r-- 1 root root   140505 Nov 15 03:29 config-3.2.0-34-generic
-rw-r--r-- 1 root root   140505 Dec  5 10:22 config-3.2.0-35-generic
drwxr-xr-x 3 root root     5120 Jan  6 13:53 grub
-rw-r--r-- 1 root root 14768089 Jul 29 14:42 initrd.img-3.2.0-27-generic
-rw-r--r-- 1 root root 14768743 Sep 18 08:40 initrd.img-3.2.0-29-generic
-rw-r--r-- 1 root root 14767969 Sep 18 08:43 initrd.img-3.2.0-30-generic
-rw-r--r-- 1 root root 14775276 Oct  9 06:44 initrd.img-3.2.0-31-generic
-rw-r--r-- 1 root root 14775559 Nov  1 08:34 initrd.img-3.2.0-32-generic
-rw-r--r-- 1 root root 14773341 Nov 15 20:15 initrd.img-3.2.0-33-generic
-rw-r--r-- 1 root root 14773683 Dec  9 12:37 initrd.img-3.2.0-34-generic
-rw-r--r-- 1 root root 14774318 Dec 18 10:13 initrd.img-3.2.0-35-generic
drwxr-xr-x 2 root root    12288 Mar 14  2012 lost+found
-rw-r--r-- 1 root root   176764 Nov 27  2011 memtest86+.bin
-rw-r--r-- 1 root root   178944 Nov 27  2011 memtest86+_multiboot.bin
-rw------- 1 root root  2882027 Jul  6  2012 System.map-3.2.0-27-generic
-rw------- 1 root root  2882108 Jul 27 10:44 System.map-3.2.0-29-generic
-rw------- 1 root root  2883362 Aug 24 10:33 System.map-3.2.0-30-generic
-rw------- 1 root root  2883401 Sep  7 09:57 System.map-3.2.0-31-generic
-rw------- 1 root root  2884076 Sep 26 15:14 System.map-3.2.0-32-generic
-rw------- 1 root root  2884306 Oct 18 10:10 System.map-3.2.0-33-generic
-rw------- 1 root root  2885127 Nov 15 03:29 System.map-3.2.0-34-generic
-rw------- 1 root root  2885822 Dec  5 10:22 System.map-3.2.0-35-generic
-rw------- 1 root root  4960848 Jul  6  2012 vmlinuz-3.2.0-27-generic
-rw------- 1 root root  4960752 Jul 27 10:44 vmlinuz-3.2.0-29-generic
-rw------- 1 root root  4963280 Aug 24 10:33 vmlinuz-3.2.0-30-generic
-rw------- 1 root root  4963792 Sep  7 09:57 vmlinuz-3.2.0-31-generic
-rw------- 1 root root  4966768 Sep 26 15:14 vmlinuz-3.2.0-32-generic
-rw------- 1 root root  4966896 Oct 18 10:10 vmlinuz-3.2.0-33-generic
-rw------- 1 root root  4967632 Nov 15 03:29 vmlinuz-3.2.0-34-generic
-rw------- 1 root root  4968400 Dec  5 10:22 vmlinuz-3.2.0-35-generic
doug@s15:~$ [COLOR=red]dpkg -l | grep linux-image[/COLOR]
rc  linux-image-3.2.0-18-generic              3.2.0-18.29                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-19-generic              3.2.0-19.31                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-20-generic              3.2.0-20.33                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-21-generic              3.2.0-21.34                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-22-generic              3.2.0-22.35                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-23-generic              3.2.0-23.36                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-24-generic              3.2.0-24.39                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-26-generic              3.2.0-26.41                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  [COLOR=red]linux-image-3.2.0-27-generic[/COLOR]              3.2.0-27.43 [COLOR=red]<<< Oldest one[/COLOR]         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-29-generic              3.2.0-29.46                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-30-generic              3.2.0-30.48                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-31-generic              3.2.0-31.50                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-32-generic              3.2.0-32.51                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-33-generic              3.2.0-33.52                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-34-generic              3.2.0-34.53                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-35-generic              3.2.0-35.55                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.22                        3.2.22-1                                   Linux kernel, version 3.2.22
rc  linux-image-3.2.22+                       3.2.22+-2                                  Linux kernel, version 3.2.22+
rc  linux-image-3.2.23                        3.2.23-1                                   Linux kernel, version 3.2.23
rc  linux-image-3.2.23+                       3.2.23+-4                                  Linux kernel, version 3.2.23+
rc  linux-image-3.5.0-030500rc1-generic       3.5.0-030500rc1.201206022335               Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-030500rc2-generic       3.5.0-030500rc2.201206082235               Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-030500rc5-generic       3.5.0-030500rc5.201206302035               Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-030500rc6-generic       3.5.0-030500rc6.201207072135               Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.5.0-030500rc7-generic       3.5.0-030500rc7.201207142035               Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-3.6.1-030601-generic          3.6.1-030601.201210071322                  Linux kernel image for version 3.6.1 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-030500rc2-generic 3.5.0-030500rc2.201206082235               Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-030500rc5-generic 3.5.0-030500rc5.201206302035               Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-030500rc6-generic 3.5.0-030500rc6.201207072135               Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.5.0-030500rc7-generic 3.5.0-030500rc7.201207142035               Linux kernel image for version 3.5.0 on 64 bit x86 SMP
rc  linux-image-extra-3.6.1-030601-generic    3.6.1-030601.201210071322                  Linux kernel image for version 3.6.1 on 64 bit x86 SMP
ii  linux-image-server                        3.2.0.35.40                                Linux kernel image on Server Equipment.
doug@s15:~$ [COLOR=red]sudo dpkg -r linux-image-3.2.0-27-generic[/COLOR]
[sudo] password for doug:
(Reading database ... 280243 files and directories currently installed.)
Removing linux-image-3.2.0-27-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-27-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-34-generic
Found initrd image: /boot/initrd.img-3.2.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-33-generic
Found initrd image: /boot/initrd.img-3.2.0-33-generic
Found linux image: /boot/vmlinuz-3.2.0-32-generic
Found initrd image: /boot/initrd.img-3.2.0-32-generic
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found memtest86+ image: /memtest86+.bin
done
doug@s15:~$ [COLOR=red]dpkg -l | grep header[/COLOR]
ii  libdw-dev                                 0.152-1ubuntu3                             libdw1 development libraries and header files
ii  libelf-dev                                0.152-1ubuntu3                             libelf1 development libraries and header files
ii  [COLOR=red]linux-headers-3.2.0-27[/COLOR]                    3.2.0-27.43                                Header files related to Linux kernel version 3.2.0
ii  [COLOR=red]linux-headers-3.2.0-27-generic[/COLOR]            3.2.0-27.43                                Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-29                    3.2.0-29.46                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-29-generic            3.2.0-29.46                                Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-30                    3.2.0-30.48                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-30-generic            3.2.0-30.48                                Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-31                    3.2.0-31.50                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-31-generic            3.2.0-31.50                                Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-32                    3.2.0-32.51                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-32-generic            3.2.0-32.51                                Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-33                    3.2.0-33.52                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-33-generic            3.2.0-33.52                                Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-34                    3.2.0-34.53                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-34-generic            3.2.0-34.53                                Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-35                    3.2.0-35.55                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-35-generic            3.2.0-35.55                                Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-server                      3.2.0.35.40                                Linux kernel headers on Server Equipment.
doug@s15:~$ [COLOR=red]sudo dpkg -r linux-headers-3.2.0-27[/COLOR]
dpkg: dependency problems prevent removal of linux-headers-3.2.0-27:
 linux-headers-3.2.0-27-generic depends on linux-headers-3.2.0-27.
dpkg: error processing linux-headers-3.2.0-27 (--remove):
 dependency problems - not removing
Errors were encountered while processing:  [COLOR=red]<<< Opps, I never remember the correct order[/COLOR]
 linux-headers-3.2.0-27
doug@s15:~$ [COLOR=red]sudo dpkg -r linux-headers-3.2.0-27-generic[/COLOR]
(Reading database ... 276112 files and directories currently installed.)
Removing linux-headers-3.2.0-27-generic ...
doug@s15:~$ [COLOR=red]sudo dpkg -r linux-headers-3.2.0-27[/COLOR]
(Reading database ... 267975 files and directories currently installed.)
Removing linux-headers-3.2.0-27 ...
doug@s15:~$ [COLOR=red]df[/COLOR]
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/s15-root 952975268 467117120 437449780  52% /
udev                   7993260        12   7993248   1% /dev
tmpfs                  3200936       756   3200180   1% /run
none                      5120         0      5120   0% /run/lock
none                   8002336         0   8002336   0% /run/shm
cgroup                 8002336         0   8002336   0% /sys/fs/cgroup
/dev/sda1               233191    166127     54623  [COLOR=red]76%[/COLOR] /boot  [COLOR=red]<<< O.K. some more space now[/COLOR]
doug@s15:~$

```

---

### Post by Futureking on 2013-01-12
You are right! My /boot is 100% full.

How you determined that which image is oldest? Here is my screenshot:
[http://postimage.org/image/zbp3s6lij/](http://postimage.org/image/zbp3s6lij/)
[IMG]http://s1.postimage.org/4u990my5r/ubuntu_error.jpg[/IMG]

---

### Post by Doug S on 2013-01-13
3.2.0-23.36 is the oldest on your system.
 
My listing was a little different, because I don't purge even older ones when I remove them.

---

### Post by Dlambert on 2013-01-13
Ubuntu Tweak Janitor or Bleachbit is what I use for cleaning my systems.

---

### Post by lisati on 2013-01-13
Installing tools to help clean things out might be a bit difficult if the disk is full.

Here's my $0.02 to start the ball rolling:
```

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

```

---

### Post by d4m1r on 2013-01-14
> **Futureking said:**
> You are right! My /boot is 100% full.

How you determined that which image is oldest? 

They go numerically so 23.36 is indeed the oldest and it goes down from there...I would recommend deleting all of them EXCEPT for 1 older kernel version, along with the latest of course.

---

### Post by LHammonds on 2013-01-15
One thing I do on a normal basis, especially after a new linux image is released, is check the drive space using "df --block-size=M"

```

# df --block-size=M
Filesystem           1M-blocks  Used Available Use% Mounted on
/dev/mapper/LVG-root     1875M  550M     1230M  31% /
udev                     2977M    1M     2977M   1% /dev
tmpfs                    1195M    1M     1194M   1% /run
none                        5M    0M        5M   0% /run/lock
none                     2986M    0M     2986M   0% /run/shm
/dev/mapper/LVG-tmp       727M   11M      679M   2% /tmp
/dev/sda1                 179M   73M       97M  43% /boot
/dev/mapper/LVG-bak       992M  607M      335M  65% /bak
/dev/mapper/LVG-home      485M    7M      454M   2% /home
/dev/mapper/LVG-opt       993M  599M      344M  64% /opt
/dev/mapper/LVG-usr      1875M  961M      819M  55% /usr
/dev/mapper/LVG-var      1875M  537M     1243M  31% /var
/dev/mapper/LVG-srv      2977M 2184M      642M  78% /srv

```Whenever I see /boot over 30% (it is at 43%), that is when I look to see how many kernels I have.  I typically only want to keep 2 (current and prior)

```

# ls -l /boot/vm*
-rw------- 1 root root 4966896 Oct 18 12:10 /boot/vmlinuz-3.2.0-33-generic
-rw------- 1 root root 4967632 Nov 15 05:29 /boot/vmlinuz-3.2.0-34-generic
-rw------- 1 root root 4968400 Dec  5 12:22 /boot/vmlinuz-3.2.0-35-generic

```Looks like I have an old one I can get rid of.....3.2.0-33....so I use the following command:

```
apt-get remove linux-image-3.2.0-33-generic
```The 1st part of the command is always the same: **apt-get remove linux-image-**

The last part matches the filename starting from the number: **3.2.0-33-generic**

Now I take a look again at /boot to verify the file was removed.

```

# ls -l /boot/vm*
-rw------- 1 root root 4967632 Nov 15 05:29 /boot/vmlinuz-3.2.0-34-generic
-rw------- 1 root root 4968400 Dec  5 12:22 /boot/vmlinuz-3.2.0-35-generic

```Looks good.  Now I verify that the consumed space was reduced.

```

# df --block-size=M
Filesystem           1M-blocks  Used Available Use% Mounted on
/dev/mapper/LVG-root     1875M  406M     1374M  23% /
udev                     2977M    1M     2977M   1% /dev
tmpfs                    1195M    1M     1194M   1% /run
none                        5M    0M        5M   0% /run/lock
none                     2986M    0M     2986M   0% /run/shm
/dev/mapper/LVG-tmp       727M   11M      679M   2% /tmp
/dev/sda1                 179M   50M      120M  30% /boot
/dev/mapper/LVG-bak       992M  607M      335M  65% /bak
/dev/mapper/LVG-home      485M    7M      454M   2% /home
/dev/mapper/LVG-opt       993M  599M      344M  64% /opt
/dev/mapper/LVG-usr      1875M  961M      819M  55% /usr
/dev/mapper/LVG-var      1875M  537M     1243M  31% /var
/dev/mapper/LVG-srv      2977M 2184M      642M  78% /srv

```Now I'm back to my 30% which is where it should be for the size of my partition with 2 kernel versions present.  Depending on the amount of space you gave /boot when it was setup, your "normal" percentage will vary.

This is one part of administration that I just would not trust a script or program to do for me so it is on my list of things I check on a normal basis.

LHammonds

---

