---
title: "NVidia 295.40 is out"
date: 2012-04-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by xebian on 2012-04-11
Here is the link [http://www.nvnews.net/vbulletin/showthread.php?t=178008](http://www.nvnews.net/vbulletin/showthread.php?t=178008)

Looks like this fixes some suspend issues and security issues as well.

---

### Post by paul_in_london on 2012-04-11
The update just came through for me on this particular install, but it's late and I'm not going to troubleshoot it right now:

```
Current status: 1 update [+1].
paul@precise-64:~$ sudo aptitude safe-upgrade                                   
The following packages will be upgraded: 
  nvidia-current 
1 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 58.6 MB of archives. After unpacking 87.0 kB will be used.
Do you want to continue? [Y/n/?] Y
Get: 1 http://ppa.launchpad.net/portis25/test/ubuntu/ precise/main nvidia-curren
t amd64 295.40-0 [58.6 MB]
Fetched 58.6 MB in 39s (1,491 kB/s)                                             
(Reading database ... 309792 files and directories currently installed.)
Preparing to replace nvidia-current 295.33-0ubuntu1.1 (using .../nvidia-current_
295.40-0_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement nvidia-current ...
dpkg: warning: unable to delete old directory '/usr/src/nvidia-current-295.33': Directory not empty
Processing triggers for man-db ...
Setting up nvidia-current (295.40-0) ...
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-295.40 DKMS files...
Building only for 3.4.0-030400rc2-generic
Building for architecture x86_64
[COLOR="Red"][B]Building initial module for 3.4.0-030400rc2-generic
Error! Bad return status for module build on kernel: 3.4.0-030400rc2-generic (x86_64)
Consult /var/lib/dkms/nvidia-current/295.40/build/make.log for more information.[/B][/COLOR]
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.4.0-030400rc2-generic
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB

                                         
Current status: 0 updates [-1].
paul@precise-64:~$
```

---

### Post by xyzzyman on 2012-04-11
You're not running a precise kernel. You'll need to download the nvidia binary and make some changes to get it to work with your mainline kernel.

---

### Post by xebian on 2012-04-11
I used the 3.4-rcN fix to get the Nvidia module to compile. Can't remember exactly where but it's on this forum awhile back.  Not sure of the mainline kernels/repo nvidia binary but I compile mine from kernel.org and download from nvidia binary.

---

