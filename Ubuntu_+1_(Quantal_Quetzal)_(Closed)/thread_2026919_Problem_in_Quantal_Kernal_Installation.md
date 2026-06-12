---
title: "Problem in Quantal Kernal Installation"
date: 2012-07-16
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Deepak J on 2012-07-16
On reading the announcement about the new Quantal kernel(3.5) 
"http://ubuntuforums.org/announcement.php?f=&a=83" ,
 I got interested in testing the new kernel and I followed the links given there and finally followed the instructions given for installation of the kernel as per "packages.qa.ubuntu.com/qatracker/milestones/223/builds/18435/downloads".

But while trying to install I end up getting the following errors and when I reboot and check the kernel version it's the same 3.2 kernel of Precise.

Tried it two times but in vain..:(

The errors that I encounter are as follows..::


Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources                    
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages             
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main amd64 Packages
  404  Not Found
Ign [http://archive.canonical.com](http://archive.canonical.com) precise/partner Translation-en
Hit [https://private-ppa.launchpad.net](https://private-ppa.launchpad.net) precise Release.gpg
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_IN
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) precise/main i386 Packages
  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/bzr-explorer-dev/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/bzr-explorer-dev/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/bzr-explorer-dev/ppa/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/bzr-explorer-dev/ppa/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/bzr-explorer-dev/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/bzr-explorer-dev/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/qbzr-dev/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/qbzr-dev/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/qbzr-dev/ppa/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/qbzr-dev/ppa/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/qbzr-dev/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/qbzr-dev/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used 


Thanks in advance....:)

---

### Post by dino99 on 2012-07-16
you might use this one instead:

[https://launchpad.net/~ubuntu-x-swat/+archive/q-lts-backport](https://launchpad.net/~ubuntu-x-swat/+archive/q-lts-backport)

---

