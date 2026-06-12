---
title: "apt-file problem"
date: 2008-05-17
forum: Server Platforms
---

### Post by mitjab on 2008-05-17
root@server:/usr/lib/postgresql/8.3/lib# sudo apt-file update
Can't get [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/Contents-i386.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/Contents-i386.gz)
Can't get [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz)
Can't get [http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz](http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz)
Can't get [http://archive.ubuntu.com/ubuntu/dists/hardy-backports/Contents-i386.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-backports/Contents-i386.gz)
Can't get [http://archive.canonical.com/ubuntu/dists/hardy/Contents-i386.gz](http://archive.canonical.com/ubuntu/dists/hardy/Contents-i386.gz)
root@server:/usr/lib/postgresql/8.3/lib#

and installation

Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 17.0kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe apt-file 2.1.0 [17.0kB]
Fetched 17.0kB in 0s (50.6kB/s)
(Reading database ... 71432 files and directories currently installed.)
Preparing to replace apt-file 2.1.0 (using .../apt-file_2.1.0_all.deb) ...
Unpacking replacement apt-file ...
Setting up apt-file (2.1.0) ...
/usr/share/apt-file/is-cache-empty: line 13: return: can only `return' from a function or sourced script


why sudo apt-file update not working for a long time?

---

