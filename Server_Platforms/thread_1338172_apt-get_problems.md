---
title: "apt-get problems"
date: 2009-11-26
forum: Server Platforms
---

### Post by rtotheototheb on 2009-11-26
Hi all,

When ever I issue the apt-get <option> command the following error occurs:

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.28-16-server (2.6.28-16.57) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-16-server
update-initramfs: failed for /boot/initrd.img-2.6.28-16-server
Failed to create initrd image.
dpkg: error processing linux-image-2.6.28-16-server (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.28-16-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

When looking at /var/log/dpkg.log the following is recorded:

2009-11-26 10:59:16 startup packages configure
2009-11-26 10:59:16 configure linux-image-2.6.28-16-server 2.6.28-16.57 2.6.28-16.57
2009-11-26 10:59:16 status half-configured linux-image-2.6.28-16-server 2.6.28-16.57

Where do I start on resolving this issue?

I have googled the problem but the majority of fixes relate to Ubuntu workstation, other versions of Ubuntu or on upgrading from one version to another.  These posts don't really match the problem I am experiencing and I'm a little apprehensive in running these fixes as this is a production server.  The server is running fine except for this one issue and don't want to cause further issues.

One interesting thread I did stumble on was:
[http://ubuntuforums.org/showthread.php?t=1206227](http://ubuntuforums.org/showthread.php?t=1206227)

Any help on this issue will be appreciated.

---

### Post by slakkie on 2009-11-26
> **rtotheototheb said:**
> 
Where do I start on resolving this issue?

I have googled the problem but the majority of fixes relate to Ubuntu workstation, other versions of Ubuntu or on upgrading from one version to another.  These posts don't really match the problem I am experiencing and I'm a little apprehensive in running these fixes as this is a production server.  The server is running fine except for this one issue and don't want to cause further issues.

One interesting thread I did stumble on was:
[http://ubuntuforums.org/showthread.php?t=1206227](http://ubuntuforums.org/showthread.php?t=1206227)

Any help on this issue will be appreciated.


Ubuntu workstation solutions can work on servers as well, since it uses the same base system. I don't know what kind of solutions you've found, but I would try some, probably you've seen posts regarding: *apt-get -f install*, that is definitely something you could run. Unless you post the solutions we can only guess what they were.. 

Could you run the following commands and post the output;

dpkg -l | grep linux-image
apt-cache policy linux-image-server 
uname -r

Many thanks.

---

### Post by rtotheototheb on 2009-11-26
Thank you for quickly replying.  I have tried the apt-get -f install command but the error still occurs.

Output from dpkg -l | grep linux-image

ii  linux-image-2.6.28-11-server              2.6.28-11.42                      Linux kernel image for version 2.6.28 on x86
ii  linux-image-2.6.28-14-server              2.6.28-14.47                      Linux kernel image for version 2.6.28 on x86
ii  linux-image-2.6.28-15-server              2.6.28-15.52                      Linux kernel image for version 2.6.28 on x86
iF  linux-image-2.6.28-16-server              2.6.28-16.57                      Linux kernel image for version 2.6.28 on x86
ii  linux-image-server                        2.6.28.16.21                      Linux kernel image on Server Equipment.

Output from apt-cache policy linux-image-server

linux-image-server:
  Installed: 2.6.28.16.21
  Candidate: 2.6.28.16.21
  Version table:
 *** 2.6.28.16.21 0
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Packages
        500 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
        100 /var/lib/dpkg/status
     2.6.28.11.15 0
        500 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Packages

Output from uname -r

2.6.28-16-server

---

### Post by slakkie on 2009-11-26
I can tell you what I would do:

Boot into another kernel, remove the kernel which is causing problems, then try to install it again. Since it is a kernel thing you would need to reboot anyway, so rebooting to an older kernel is acceptable IMO.

If this is a machine which needs to be up, it would require maintenance at night so users don't notice the outage.

---

### Post by rtotheototheb on 2009-11-27
Hi Slakkie,

Resolved the issue in the end and I wasn't up all night either.  It took about 15 minutes in total including the reboots :)

I booted the server using the previous kernel version and followed the instructions from the 1st link on dstew's forum post dated July 14th, 2009.

[http://ubuntuforums.org/showthread.php?t=1206227&page=2]("http://ubuntuforums.org/showthread.php?t=1206227&page=2")

apt-get <option> now runs without any issues, sweet! :D

Thanks for all your help on this problem.

---

### Post by slakkie on 2009-11-27
Nice, don't forget to add [SOLVED] to the topic title, so people know the issue has been solved.

---

