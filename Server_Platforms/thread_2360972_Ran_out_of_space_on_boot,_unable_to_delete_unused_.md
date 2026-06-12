---
title: "Ran out of space on /boot, unable to delete unused kernels"
date: 2017-05-10
forum: Server Platforms
---

### Post by a penguin on 2017-05-10
My apologies for the large post, I included as much data as I could.

I'm dealing with an Ubuntu 16.04 LTS server that I've been trying to upgrade for a while now, but I'm just not getting anywhere.

It all started with running out of space on /boot while running sudo apt-get upgrade.

Commands I've tried:

I've since tried to remove old kernels using dpkg --purge, which results in a dependency error no matter which image I select:

dpkg --purge linux-image-4.4.0-38-generic
```
dpkg: error: requested operation requires superuser privilege
sudo dpkg --purge linux-image-4.4.0-38-generic
dpkg: dependency problems prevent removal of linux-image-4.4.0-38-generic:
linux-image-extra-4.4.0-38-generic depends on linux-image-4.4.0-38-generic.


dpkg: error processing package linux-image-4.4.0-38-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-4.4.0-38-generic



```

I've also tried (after the dpkg command), without any success:

sudo apt-get -f install
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic linux-image-4.4.0-31-generic linux-image-extra-4.4.0-31-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-4.4.0-53-generic linux-image-4.4.0-77-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools linux-headers-4.4.0-53-generic
The following NEW packages will be installed:
  linux-image-4.4.0-53-generic linux-image-4.4.0-77-generic
0 upgraded, 2 newly installed, 0 to remove and 141 not upgraded.
8 not fully installed or removed.
Need to get 57.8 MB/79.7 MB of archives.
After this operation, 124 MB of additional disk space will be used.
Do you want to continue? [Y/n]

```

sudo apt-get purge
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-53-generic : Depends: linux-image-4.4.0-53-generic but it is not installed
 linux-image-extra-4.4.0-77-generic : Depends: linux-image-4.4.0-77-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-77-generic but it is not installed
                       Recommends: thermald but it is not installed
E: Unmet dependencies. Try using -f.



```

sudo apt-get purge -f
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-31 linux-headers-4.4.0-31-generic linux-image-4.4.0-31-generic linux-image-extra-4.4.0-31-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  linux-image-4.4.0-53-generic linux-image-4.4.0-77-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools linux-headers-4.4.0-53-generic
The following NEW packages will be installed:
  linux-image-4.4.0-53-generic linux-image-4.4.0-77-generic
0 upgraded, 2 newly installed, 0 to remove and 141 not upgraded.
8 not fully installed or removed.
Need to get 57.8 MB/79.7 MB of archives.
After this operation, 124 MB of additional disk space will be used.
Do you want to continue? [Y/n]
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-4.4.0-53-generic amd64 4.4.0-53.74 [19.2 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 linux-image-extra-4.4.0-53-generic amd64 4.4.0-53.74 [38.6 MB]
Fetched 57.8 MB in 1min 37s (590 kB/s)
(Reading database ... 382519 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-77-generic_4.4.0-77.98_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-77-generic (4.4.0-77.98) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-77-generic_4.4.0-77.98_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-4.4.0-77-generic' to '/boot/System.map-4.4.0-77-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
Preparing to unpack .../linux-image-4.4.0-53-generic_4.4.0-53.74_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-53-generic (4.4.0-53.74) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-53-generic_4.4.0-53.74_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-4.4.0-53-generic' to '/boot/System.map-4.4.0-53-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-77-generic_4.4.0-77.98_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-53-generic_4.4.0-53.74_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```


Does anyone have any suggestions as how to proceed?

Additional Information:

uname -r
```
4.4.0-51-generic
```

df
```
Filesystem                    1K-blocks    Used Available Use% Mounted on
udev                             995884       0    995884   0% /dev
tmpfs                            203056    5968    197088   3% /run
/dev/mapper/SRVRNAME--vg-root  28271624 5089384  21723040  19% /
tmpfs                           1015272      12   1015260   1% /dev/shm
tmpfs                              5120       0      5120   0% /run/lock
tmpfs                           1015272       0   1015272   0% /sys/fs/cgroup
/dev/sda1                        482922  482349         0 100% /boot
tmpfs                            203056       0    203056   0% /run/user/1000

```
ls -la /boot
```
total 473197
drwxr-xr-x  4 root root     4096 May 10 09:55 .
drwxr-xr-x 23 root root     4096 Nov 30 16:35 ..
-rw-r--r--  1 root root  1239577 Apr 18  2016 abi-4.4.0-21-generic
-rw-r--r--  1 root root  1240018 Jun 24  2016 abi-4.4.0-28-generic
-rw-r--r--  1 root root  1240067 Jul 12  2016 abi-4.4.0-31-generic
-rw-r--r--  1 root root  1241623 Jul 27  2016 abi-4.4.0-34-generic
-rw-r--r--  1 root root  1241960 Aug 11  2016 abi-4.4.0-36-generic
-rw-r--r--  1 root root  1242262 Sep  6  2016 abi-4.4.0-38-generic
-rw-r--r--  1 root root  1242701 Oct  7  2016 abi-4.4.0-42-generic
-rw-r--r--  1 root root  1242701 Oct 19  2016 abi-4.4.0-45-generic
-rw-r--r--  1 root root  1243086 Oct 26  2016 abi-4.4.0-47-generic
-rw-r--r--  1 root root  1243479 Nov 24 16:12 abi-4.4.0-51-generic
-rw-r--r--  1 root root   189412 Apr 18  2016 config-4.4.0-21-generic
-rw-r--r--  1 root root   189533 Jun 24  2016 config-4.4.0-28-generic
-rw-r--r--  1 root root   189558 Jul 12  2016 config-4.4.0-31-generic
-rw-r--r--  1 root root   189676 Jul 27  2016 config-4.4.0-34-generic
-rw-r--r--  1 root root   189696 Aug 11  2016 config-4.4.0-36-generic
-rw-r--r--  1 root root   189732 Sep  6  2016 config-4.4.0-38-generic
-rw-r--r--  1 root root   189760 Oct  7  2016 config-4.4.0-42-generic
-rw-r--r--  1 root root   189760 Oct 19  2016 config-4.4.0-45-generic
-rw-r--r--  1 root root   189809 Oct 26  2016 config-4.4.0-47-generic
-rw-r--r--  1 root root   189877 Nov 24 16:12 config-4.4.0-51-generic
drwxr-xr-x  5 root root     1024 Nov 30 16:35 grub
-rw-r--r--  1 root root 35727575 Jun 29  2016 initrd.img-4.4.0-21-generic
-rw-r--r--  1 root root 35739941 Jun 29  2016 initrd.img-4.4.0-28-generic
-rw-r--r--  1 root root 35714432 Jul 15  2016 initrd.img-4.4.0-31-generic
-rw-r--r--  1 root root 35736619 Aug  9  2016 initrd.img-4.4.0-34-generic
-rw-r--r--  1 root root 35743788 Aug 30  2016 initrd.img-4.4.0-36-generic
-rw-r--r--  1 root root 35744265 Sep 29  2016 initrd.img-4.4.0-38-generic
-rw-r--r--  1 root root 36150688 Oct 11  2016 initrd.img-4.4.0-42-generic
-rw-r--r--  1 root root 36149152 Oct 20  2016 initrd.img-4.4.0-45-generic
-rw-r--r--  1 root root 36202174 Nov 10 00:27 initrd.img-4.4.0-47-generic
-rw-r--r--  1 root root 36201630 Nov 30 16:35 initrd.img-4.4.0-51-generic
drwx------  2 root root    12288 Jun 23  2016 lost+found
-rw-------  1 root root  3853719 Apr 18  2016 System.map-4.4.0-21-generic
-rw-------  1 root root  3859655 Jun 24  2016 System.map-4.4.0-28-generic
-rw-------  1 root root  3866473 Jul 12  2016 System.map-4.4.0-31-generic
-rw-------  1 root root  3866644 Jul 27  2016 System.map-4.4.0-34-generic
-rw-------  1 root root  3867829 Aug 11  2016 System.map-4.4.0-36-generic
-rw-------  1 root root  3869329 Sep  6  2016 System.map-4.4.0-38-generic
-rw-------  1 root root  3869895 Oct  7  2016 System.map-4.4.0-42-generic
-rw-------  1 root root  3869895 Oct 19  2016 System.map-4.4.0-45-generic
-rw-------  1 root root  3873447 Oct 26  2016 System.map-4.4.0-47-generic
-rw-------  1 root root  3874377 Nov 24 16:12 System.map-4.4.0-51-generic
-rw-------  1 root root  7013968 Apr 18  2016 vmlinuz-4.4.0-21-generic
-rw-------  1 root root  7026864 Jun 24  2016 vmlinuz-4.4.0-28-generic
-rw-------  1 root root  7047504 Jul 12  2016 vmlinuz-4.4.0-31-generic
-rw-------  1 root root  7046160 Jul 27  2016 vmlinuz-4.4.0-34-generic
-rw-------  1 root root  7045472 Aug 11  2016 vmlinuz-4.4.0-36-generic
-rw-------  1 root root  7051680 Sep  6  2016 vmlinuz-4.4.0-38-generic
-rw-------  1 root root  7053472 Oct  7  2016 vmlinuz-4.4.0-42-generic
-rw-------  1 root root  7054208 Oct 19  2016 vmlinuz-4.4.0-45-generic
-rw-------  1 root root  7060896 Oct 26  2016 vmlinuz-4.4.0-47-generic
-rw-------  1 root root  7064208 Nov 24 16:12 vmlinuz-4.4.0-51-generic

```

dpkg -l | grep linux-
```
ii  linux-base                         4.0ubuntu1                      all          Linux image base package
ii  linux-firmware                     1.157.4                         all          Firmware for Linux kernel drivers
iU  linux-generic                      4.4.0.77.83                     amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-21             4.4.0-21.37                     all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-21-generic     4.4.0-21.37                     amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-28             4.4.0-28.47                     all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-28-generic     4.4.0-28.47                     amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-31             4.4.0-31.50                     all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-31-generic     4.4.0-31.50                     amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-34             4.4.0-34.53                     all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-34-generic     4.4.0-34.53                     amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-36             4.4.0-36.55                     all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-36-generic     4.4.0-36.55                     amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-38             4.4.0-38.57                     all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-38-generic     4.4.0-38.57                     amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-42             4.4.0-42.62                     all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-42-generic     4.4.0-42.62                     amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-45             4.4.0-45.66                     all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-45-generic     4.4.0-45.66                     amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-47             4.4.0-47.68                     all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-47-generic     4.4.0-47.68                     amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-51             4.4.0-51.72                     all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-51-generic     4.4.0-51.72                     amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-4.4.0-77             4.4.0-77.98                     all          Header files related to Linux kernel version 4.4.0
iU  linux-headers-4.4.0-77-generic     4.4.0-77.98                     amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-generic              4.4.0.77.83                     amd64        Generic Linux kernel headers
pi  linux-image-4.4.0-21-generic       4.4.0-21.37                     amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
pi  linux-image-4.4.0-28-generic       4.4.0-28.47                     amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
pi  linux-image-4.4.0-31-generic       4.4.0-31.50                     amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
pi  linux-image-4.4.0-34-generic       4.4.0-34.53                     amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
pi  linux-image-4.4.0-36-generic       4.4.0-36.55                     amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-38-generic       4.4.0-38.57                     amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-42-generic       4.4.0-42.62                     amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-generic       4.4.0-45.66                     amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic       4.4.0-47.68                     amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-51-generic       4.4.0-51.72                     amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-21-generic 4.4.0-21.37                     amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-28-generic 4.4.0-28.47                     amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-31-generic 4.4.0-31.50                     amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-34-generic 4.4.0-34.53                     amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-36-generic 4.4.0-36.55                     amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-38-generic 4.4.0-38.57                     amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-42-generic 4.4.0-42.62                     amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-45-generic 4.4.0-45.66                     amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-47-generic 4.4.0-47.68                     amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-51-generic 4.4.0-51.72                     amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rH  linux-image-extra-4.4.0-53-generic 4.4.0-53.74                     amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-77-generic 4.4.0-77.98                     amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                4.4.0.77.83                     amd64        Generic Linux kernel image




```

---

### Post by Autodave on 2017-05-10
"sudo apt autoremove --purge"  is what I use.

---

### Post by howefield on 2017-05-10
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by a penguin on 2017-05-10
[SIZE=2][COLOR=#000080]**sudo apt autoremove --purge**[/COLOR][/SIZE]```

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-extra-4.4.0-53-generic : Depends: linux-image-4.4.0-53-generic but it is not installed
 linux-image-extra-4.4.0-77-generic : Depends: linux-image-4.4.0-77-generic but it is not installed
 linux-image-generic : Depends: linux-image-4.4.0-77-generic but it is not installed
                       Recommends: thermald but it is not installed
E: Unmet dependencies. Try using -f.
```


[COLOR=#000080][SIZE=2]**sudo apt autoremove --purge -f**[/SIZE][/COLOR]```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-image-4.4.0-53-generic linux-image-4.4.0-77-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools linux-headers-4.4.0-53-generic
The following packages will be REMOVED:
  linux-headers-4.4.0-31* linux-headers-4.4.0-31-generic* linux-image-4.4.0-31-generic* linux-image-extra-4.4.0-31-generic*
The following NEW packages will be installed:
  linux-image-4.4.0-53-generic linux-image-4.4.0-77-generic
0 upgraded, 2 newly installed, 4 to remove and 141 not upgraded.
8 not fully installed or removed.
Need to get 0 B/79.7 MB of archives.
After this operation, 171 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 382519 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-77-generic_4.4.0-77.98_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-77-generic (4.4.0-77.98) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-77-generic_4.4.0-77.98_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-4.4.0-77-generic' to '/boot/System.map-4.4.0-77-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
Preparing to unpack .../linux-image-4.4.0-53-generic_4.4.0-53.74_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-53-generic (4.4.0-53.74) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.4.0-53-generic_4.4.0-53.74_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-4.4.0-53-generic' to '/boot/System.map-4.4.0-53-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-4.4.0-77-generic_4.4.0-77.98_amd64.deb
 /var/cache/apt/archives/linux-image-4.4.0-53-generic_4.4.0-53.74_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Had my hopes up when it prompted me that this would clear up some space, but no luck :(

---

### Post by sp40140 on 2017-05-10
Try to manually delete these two files and then re-run the command again:
/var/cache/apt/archives/linux-image-4.4.0-77-generic_4.4.0-77.98_amd64.deb
/var/cache/apt/archives/linux-image-4.4.0-53-generic_4.4.0-53.74_amd64.deb

---

### Post by darkod on 2017-05-10
Forget all of the above. What you really need to do is free some space in /boot, after that apt-get will work again and will sort itself out.

Since you are booting kernel -51- anyway, I suggest you delete 3 oldest kernels. If you notice in /boot, the biggest files are initrd.img and vmlinuz, ignore the rest because they don't help much in freeing space.

So, log in, make yourself root, and start deleting:
```
sudo -i
cd /boot
rm initrd.img-4.4.0-21-generic
rm initrd.img-4.4.0-28-generic
rm initrd.img-4.4.0-31-generic
rm vmlinuz-4.4.0-21-generic
rm vmlinuz-4.4.0-28-generic
rm vmlinuz-4.4.0-31-generic
```

That should give you around 120MB which is enough apt-get to start working.

Do not try to add anything new yet, first fix it with:
```
apt-get install -f
```

I didn't use sudo above assuming you are still root.

Once you get apt-get in working state, clean up all unnecessary packages/files with:
```
sudo apt-get autoremove
```

That will automatically remove all unnecessary kernels and free up bunch of space.

---

### Post by a penguin on 2017-05-10
Ran into trouble with 2nd command (only including the df outputs for reference):

df -h
```

Filesystem                     Size  Used Avail Use% Mounted on
udev                           973M     0  973M   0% /dev
tmpfs                          199M  5.9M  193M   3% /run
/dev/mapper/SVRNAME --vg-root   27G  5.1G   21G  20% /
tmpfs                          992M   12K  992M   1% /dev/shm
tmpfs                          5.0M     0  5.0M   0% /run/lock
tmpfs                          992M     0  992M   0% /sys/fs/cgroup
/dev/sda1                      472M  349M  100M  78% /boot
tmpfs                          100K     0  100K   0% /run/lxcfs/controllers
tmpfs                          199M     0  199M   0% /run/user/1000

```

**[COLOR=#000080][SIZE=2]apt-get install -f[/SIZE][/COLOR]**
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-image-4.4.0-53-generic linux-image-4.4.0-77-generic
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools linux-headers-4.4.0-53-generic
The following NEW packages will be installed:
  linux-image-4.4.0-53-generic linux-image-4.4.0-77-generic
0 upgraded, 2 newly installed, 0 to remove and 141 not upgraded.
8 not fully installed or removed.
Need to get 0 B/79.7 MB of archives.
After this operation, 124 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 382519 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-77-generic_4.4.0-77.98_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-77-generic (4.4.0-77.98) ...
Preparing to unpack .../linux-image-4.4.0-53-generic_4.4.0-53.74_amd64.deb ...
Done.
Unpacking linux-image-4.4.0-53-generic (4.4.0-53.74) ...
Setting up linux-image-4.4.0-77-generic (4.4.0-77.98) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-77-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-77-generic
Found initrd image: /boot/initrd.img-4.4.0-77-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
done
Setting up linux-image-extra-4.4.0-77-generic (4.4.0-77.98) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-77-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-77-generic /boot/vmlinuz-4.4.0-77-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-77-generic
Found initrd image: /boot/initrd.img-4.4.0-77-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
done
Setting up linux-image-generic (4.4.0.77.83) ...
Setting up linux-headers-4.4.0-77 (4.4.0-77.98) ...
Setting up linux-headers-4.4.0-77-generic (4.4.0-77.98) ...
Setting up linux-headers-generic (4.4.0.77.83) ...
Setting up linux-generic (4.4.0.77.83) ...
Setting up linux-image-extra-4.4.0-51-generic (4.4.0-51.72) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-51-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-51-generic /boot/vmlinuz-4.4.0-51-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-77-generic
Found initrd image: /boot/initrd.img-4.4.0-77-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
done
Setting up linux-image-4.4.0-53-generic (4.4.0-53.74) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-53-generic
W: mdadm: /etc/mdadm/mdadm.conf defines no arrays.
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-53-generic /boot/vmlinuz-4.4.0-53-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-77-generic
Found initrd image: /boot/initrd.img-4.4.0-77-generic
Found linux image: /boot/vmlinuz-4.4.0-53-generic
Found initrd image: /boot/initrd.img-4.4.0-53-generic
Found linux image: /boot/vmlinuz-4.4.0-51-generic
Found initrd image: /boot/initrd.img-4.4.0-51-generic
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-45-generic
Found initrd image: /boot/initrd.img-4.4.0-45-generic
Found linux image: /boot/vmlinuz-4.4.0-42-generic
Found initrd image: /boot/initrd.img-4.4.0-42-generic
Found linux image: /boot/vmlinuz-4.4.0-38-generic
Found initrd image: /boot/initrd.img-4.4.0-38-generic
Found linux image: /boot/vmlinuz-4.4.0-36-generic
Found initrd image: /boot/initrd.img-4.4.0-36-generic
Found linux image: /boot/vmlinuz-4.4.0-34-generic
Found initrd image: /boot/initrd.img-4.4.0-34-generic
done
dpkg: error processing package linux-image-extra-4.4.0-53-generic (--configure):
 package linux-image-extra-4.4.0-53-generic is not ready for configuration
 cannot configure (current status 'half-installed')
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

df
```
Filesystem                    1K-blocks    Used Available Use% Mounted on
udev                             995884       0    995884   0% /dev
tmpfs                            203056    5980    197076   3% /run
/dev/mapper/SRVRNAME--vg-root  28271624 5378480  21433944  21% /
tmpfs                           1015272      12   1015260   1% /dev/shm
tmpfs                              5120       0      5120   0% /run/lock
tmpfs                           1015272       0   1015272   0% /sys/fs/cgroup
/dev/sda1                        482922  427730     30258  94% /boot
tmpfs                               100       0       100   0% /run/lxcfs/controllers
tmpfs                            203056       0    203056   0% /run/user/1000



```

Can I force remove it?

[COLOR=#000080][SIZE=2]**dpkg --remove --force-remove-reinstreq --dry-run linux-image-extra-4.4.0-53-generic**[/SIZE][/COLOR]
```

(Reading database ... 384564 files and directories currently installed.)
Would remove or purge linux-image-extra-4.4.0-53-generic (4.4.0-53.74) ...

```

---

### Post by darkod on 2017-05-10
You can try force remove or simply purge if apt-get is still working. It ate little bit of the free space but should be OK still. Give it a shot...

---

### Post by ian-weisser on 2017-05-10
Sigh.

Seems like you were on the right track with the very first thing you tried.
The error message told you exactly what you needed to do.

> **a penguin said:**
> [COLOR=#000080]**dpkg --purge linux-image-4.4.0-38-generic**[/COLOR]
```
dpkg: error: requested operation requires superuser privilege
admin@SRVRNAME:/boot$ sudo dpkg --purge linux-image-4.4.0-38-generic
[sudo] password for admin:
dpkg: dependency problems prevent removal of linux-image-4.4.0-38-generic:
[B] linux-image-extra-4.4.0-38-generic depends on linux-image-4.4.0-38-generic.
[/B]
```

You merely needed to uninstall BOTH packages using dpkg
```
sudo dpkg --remove linux-image-4.4.0-38-generic linux-image-extra-4.4.0-38-generic
```

Then, having freed up plenty of space for apt to work,
```
sudo apt autoremove
```

---

### Post by a penguin on 2017-05-10
I actually tried that on every single image not in use, and it just wouldn't let me (similar results as the --purge option).  I didn't mention it as I had forgotten about that one.

That said, it looks like removing [COLOR=#000000][FONT=&amp]linux-image-extra-4.4.0-53-generic after manually creating space seems to finally have done the job.

I wonder why Ubuntu Server creates such small boot partitions, but my mistake for not tracking disk space.

Marked as solved.[/FONT][/COLOR]

---

### Post by ian-weisser on 2017-05-10
Ubuntu Server, by default, does not create /boot partitions at all.
The problem occurs when admins choose encryption or LVM...not realizing that the system cannot boot directly from those.

Tracking your disk space is indeed wise.

---

### Post by a penguin on 2017-05-10
So should I avoid using LVM on production servers?  There must be a reason why it doesn't create a properly sized boot partition when using the LVM option.

---

### Post by darkod on 2017-05-10
LVM is very useful, but don't depend on the guided method. Use your own manual partitioning. That way YOU select /boot partition size. Make it 1-2GB and with occasional space check, you are OK.

The guided LVM method makes really, really small /boot. Something should have changed long time ago since disks are huge years ago. Maybe this method was OK 10years ago, but now...

---

### Post by cariboo on 2017-05-10
I use lvm on my server, but I have a separate O/S drive. I create the lvm manually to get what I wanted.

To prevent similar problems from occurring, I'd suggest giving ucaresystem-core a try, it does updates, upgrades and removes unused kernels and files all with only one command:

```
sudo ucaresystem-core
```

it is available here:

[https://utappia.org/2016/03/28/ucaresystem-core-v3-0-released-and-available-in-ppa/](https://utappia.org/2016/03/28/ucaresystem-core-v3-0-released-and-available-in-ppa/)

---

### Post by ian-weisser on 2017-05-10
> **a penguin said:**
> There must be a reason why it doesn't create a properly sized boot partition when using the LVM option.

Well, /boot *is* properly sized for the vast majority of encryption and LVM users. It can hold at least three, with room to spare.
A handy little script runs daily and happily autoremoves old kernels when the occasional upgrade occurs.
I have tested that little script exhaustively since it first appeared in 16.04, and it works perfectly on all my test systems every time.

I have found only two conditions under which that little kernel-autoremove script doesn't work:
1) Kernels that are ineligible for autoremoval due to an apt dependency
2) The admin has inadvertently disabled the script, usually by diasbling or uninstalling unattended-upgrades.

Both of those conditions are *very* hard for beginners to diagnose, and neither emit any useful warnings.
Kernel autoremovals, if working, are logged in /var/log/unattended-upgrades

The most common workaround is to run 'sudo apt autoremove' regularly - once a month or once a quarter, or, cleverly, after a kernel update.

The ability to boot from LVM has recently been demonstrated, so a permanent elimination of separate /boot partitions may be pending.

---

### Post by thomas-danzl on 2018-03-07
thanks! this worked for me :) on 17.10

---

### Post by luiscordi on 2018-08-05
Thanks darkod!
Your answer solved my problem!

---

### Post by coffeecat on 2018-08-05
Back to sleep, venerable thread.

Closed.

---

