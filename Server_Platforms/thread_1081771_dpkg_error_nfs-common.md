---
title: "dpkg error nfs-common"
date: 2009-02-26
forum: Server Platforms
---

### Post by cscomplab on 2009-02-26
try to install nfs kernel server, nfs common is dependancy.  the startup script for nfs-common returns error status 1.  linux32 is not installed, util-linux is installed.  this is a 64-bit server.  what gives?

---

### Post by cscomplab on 2009-03-05
We are trying to install the nfs-common package on a 64 bit server edition of ubuntu.

I type "sudo apt-get install nfs-kernel-server" (nfs-common is a dependency)

Here is the output:
"setting up nfs-common...
*starting nfs-common utilities             [FAIL]
invoke -rc.d: initscript nfs-common; action "start" failed
dpkg : error processoing nfs-common (--configure):
    subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of nfs-kernel-server:

What is going on here?  Why isn't nfs-common configuered?  How can I configure it?

---

