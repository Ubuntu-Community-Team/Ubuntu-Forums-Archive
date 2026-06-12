---
title: "vmware-server 2 on 8.04 x64"
date: 2009-06-29
forum: Virtualisation
---

### Post by mntgoat on 2009-06-29
I am trying to install vmware-server2 on ubuntu 8.04 x64 and I am dying at the command below, does anyone know what I can do to fix it? 
Thanks,[INDENT]user@systemr:/$ sudo apt-get install build-essential linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages will be upgraded:
  linux-headers-2.6.24-23-server
1 upgraded, 0 newly installed, 0 to remove and 53 not upgraded.
Need to get 669kB of archives.
After this operation, 0B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main linux-headers-2.6.24-23-server 2.6.24-23.52 [669kB]
Fetched 669kB in 6s (99.3kB/s)                                                                                                                                                                                                              
(Reading database ... 49801 files and directories currently installed.)
Preparing to replace linux-headers-2.6.24-23-server 2.6.24-23.48 (using .../linux-headers-2.6.24-23-server_2.6.24-23.52_amd64.deb) ...
Unpacking replacement linux-headers-2.6.24-23-server ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.24-23-server_2.6.24-23.52_amd64.deb (--unpack):
 unable to make backup symlink for `./usr/src/linux-headers-2.6.24-23-server/scripts/kconfig/gconf.glade': No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.24-23-server_2.6.24-23.52_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/INDENT]

---

