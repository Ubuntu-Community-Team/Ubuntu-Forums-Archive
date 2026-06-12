---
title: "initramfs-tools package problem while upgrading (dapper/edgy)"
date: 2007-03-20
forum: Server Platforms
---

### Post by ariston on 2007-03-20
I recently did an upgrade from dapper to edgy, but am having some problems with initramfs-tools. I've tried to resolve with dselect, but the problem seems out of my reach.

Does anyone have any experience with this issue, or know of any workarounds? 

Thanks.....


```
watts:/etc/apt# apt-get -u install initramfs-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  initramfs-tools
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
14 not fully installed or removed.
Need to get 50.1kB of archives.
After unpacking 356kB of additional disk space will be used.
Get: 1 http://us.archive.ubuntu.com edgy/main initramfs-tools 0.69ubuntu20 [50.1kB]
Fetched 50.1kB in 1s (34.2kB/s)         
(Reading database ... 55339 files and directories currently installed.)
Unpacking initramfs-tools (from .../initramfs-tools_0.69ubuntu20_all.deb) ...
**sed: no input files**
dpkg: error processing /var/cache/apt/archives/initramfs-tools_0.69ubuntu20_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 4
Errors were encountered while processing:
 /var/cache/apt/archives/initramfs-tools_0.69ubuntu20_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

