---
title: "vmware workstation 6.5.1 build-126130  failed"
date: 2008-12-31
forum: Virtualisation
---

### Post by p4cldba on 2008-12-31
Hi,

my laptop is running ubuntu 8.10 
and i did  as below

#

sudo aptitude install build-essential linux-kernel-headers linux-kernel-devel

gksudo bash ./VMware-Workstation-6.5.0-118166.i386.bundle 

#


but the installation failed . with this snippet from the logfile .any suggestions. 

thanks in advance.
Built vsock module
Using 2.6.x kernel build system.
Using 2.6.x kernel build system.
Using 2.6.x kernel build system.
Using 2.6.x kernel build system.
Using 2.6.x kernel build system.
/tmp/vmware-root/modules/vsock-only/linux/util.c: In function ‘VSockVmciLogPkt’:
/tmp/vmware-root/modules/vsock-only/linux/util.c:157: warning: format not a string literal and no format arguments
Successfully installed kernel modules
[vmware-workstation 6.5.1] Installation failed, rolling back installation.
VMware DiskMount Utility version 6.5.1, build-126130

---

