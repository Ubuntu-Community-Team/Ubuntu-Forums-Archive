---
title: "linux-firmware and amd-microcode can not live nicely together anymore..."
date: 2013-01-30
forum: Ubuntu Development Version
---

### Post by zika on 2013-01-30
```
Preparing to replace linux-firmware 1.99 (using .../linux-firmware_1.100_all.deb) ...
Unpacking replacement linux-firmware ...
dpkg: error processing /var/cache/apt/archives/linux-firmware_1.100_all.deb (--unpack):
 trying to overwrite '/lib/firmware/amd-ucode/microcode_amd_fam15h.bin', which is also in package amd64-microcode 1.20120910-2
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
``````
:~$ sudo apt-get purge amd64-microcode 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  amd64-microcode*
0 upgraded, 0 newly installed, 1 to remove and 8 not upgraded.
After this operation, 97.3 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 315733 files and directories currently installed.)
Removing amd64-microcode ...
update-initramfs: deferring update (trigger activated)
Purging configuration files for amd64-microcode ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-030800rc5-generic

``````
Resolving dependencies...                
The following packages will be upgraded:
  linux-firmware 
1 packages upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 21.1 MB of archives. After unpacking 815 kB will be used.
Do you want to continue? [Y/n/?] 
Get: 1 http://archive.ubuntu.com/ubuntu/ raring/main linux-firmware all 1.100 [21.1 MB]
Fetched 21.1 MB in 11s (1,893 kB/s)                                             
(Reading database ... 315722 files and directories currently installed.)
Preparing to replace linux-firmware 1.99 (using .../linux-firmware_1.100_all.deb) ...
Unpacking replacement linux-firmware ...
Setting up linux-firmware (1.100) ...
``````
:~$ sudo apt-get install amd64-microcode 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  amd64-microcode
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
Need to get 28.0 kB of archives.
After this operation, 97.3 kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com/ubuntu/ raring/multiverse amd64-microcode amd64 1.20120910-2 [28.0 kB]
Fetched 28.0 kB in 0s (208 kB/s)         
Selecting previously unselected package amd64-microcode.
(Reading database ... 315857 files and directories currently installed.)
Unpacking amd64-microcode (from .../amd64-microcode_1.20120910-2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/amd64-microcode_1.20120910-2_amd64.deb (--unpack):
 trying to overwrite '/lib/firmware/amd-ucode/microcode_amd.bin', which is also in package linux-firmware 1.100
Errors were encountered while processing:
 /var/cache/apt/archives/amd64-microcode_1.20120910-2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Harry33 on 2013-01-30
That is true.
Meaning at least parts of amd64-microcode has been taken into linux-firmware package.
So, we do not need to install amd64-microcode any longer, I guess.

---

### Post by jppr on 2013-01-30
There is the amd-microcode change...

[https://lists.ubuntu.com/archives/raring-changes/2013-January/004895.html](https://lists.ubuntu.com/archives/raring-changes/2013-January/004895.html)

---

### Post by zika on 2013-01-30
> **jppr said:**
> There is the amd-microcode change...

[https://lists.ubuntu.com/archives/raring-changes/2013-January/004895.html](https://lists.ubuntu.com/archives/raring-changes/2013-January/004895.html)Yes, I've read that but there is a proper way to introduce that and make nice transition... Not a big deal, just heads_up...

---

