---
title: "404 not found, and MD5Sum mismatches"
date: 2005-10-17
forum: Repositories &amp; Backports
---

### Post by pacice on 2005-10-17
have tried to apt-get update, and got the following error messages.
What do I do to fix these.

Thanks
PACICE


> Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary-updates/main Sources
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
  404 Not Found
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hoary-updates/restricted Sources
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
  404 Not Found
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
  404 Not Found
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
  404 Not Found
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Hit [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Fetched 137kB in 3s (34.6kB/s)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz)  MD5Su m mismatch
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz)  MD5Sum mism atch
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz)  M D5Sum mismatch
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages). gz  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Package](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Package) s.gz  404 Not Found
Failed to fetch [http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Package](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Package) s.gz  404 Not Found
Reading package lists... Done
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt /lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file o r directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib /apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No suc h file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


---

