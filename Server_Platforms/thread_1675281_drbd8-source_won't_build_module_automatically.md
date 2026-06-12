---
title: "drbd8-source won't build module automatically"
date: 2011-01-25
forum: Server Platforms
---

### Post by tavasti on 2011-01-25
I have ubuntu 10.04 server installed, and I'm trying to set up drbd.
Unfortunately drbd8-source claims I don't have kernel sources installed. 
Any ideas what is missing?

root@sr1:~# dpkg-reconfigure drbd8-source
Removing all [drbd8-8.3.7] DKMS Modules
Done.
Loading new drbd8-8.3.7 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-27-server
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.

root@sr1:~# COLUMNS=140 dpkg -l linux-source\*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                          Version                       Description
+++-=============================-=============================-==========================================================================
ii  linux-source                  2.6.32.27.29                  Linux kernel source with Ubuntu patches
un  linux-source-2.6              <none>                        (no description available)
ii  linux-source-2.6.32           2.6.32-27.49                  Linux kernel source for version 2.6.32 with Ubuntu patches

---

### Post by tavasti on 2011-01-25
aptitude install linux-headers-server fixed the problem

---

