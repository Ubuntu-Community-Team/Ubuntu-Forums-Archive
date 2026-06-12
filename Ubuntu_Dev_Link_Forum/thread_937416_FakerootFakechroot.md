---
title: "Fakeroot/Fakechroot"
date: 2008-10-03
forum: Ubuntu Dev Link Forum
---

### Post by sarvi on 2008-10-03
I on a Redhat machine and just debootstrap'ed a directory with 
debian/Etch release, using fakeroot/fakechroot

The debootstrap'ing went through fine and I am able fakeroot/fakechroot into the directory.

apt seems installed and I can apt-get update/upgrade.

But when I try to do apt-get install vim or any other application 
I get the error below.

Does anyone know if there is any problem with doing apt-get stuff with fakeroot/fakechroot.

OR if fakeroot/fakechroot has a problem working with mounted filesystems?

sarvi@sjc-lds-251:/$ apt-get install strace
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  strace
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 95.4kB of archives.
After unpacking 254kB of additional disk space will be used.
E: Couldn't determine free space in /var/cache/apt/archives/ - statvfs (2 No such file or directory)
sarvi@sjc-lds-251:/$


Thanks,
Sarvi

---

