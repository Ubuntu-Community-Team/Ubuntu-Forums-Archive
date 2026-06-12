---
title: "SCST Kernel Patching in 10.10"
date: 2010-10-22
forum: Server Platforms
---

### Post by pneumatic on 2010-10-22
Does anyone know how to run SCST (2.0 branch) in 10.10?  I get HUNK errors when trying to patch the kernel with their 2.6.35 patch.  I am up and running with STGT right now but I really like the SCST approach better and would prefer to run that if at all possible.

I need to use 10.10 in order to get the mvsas fixes present in the new kernel.

---

### Post by so|326 on 2010-11-24
Bump

---

### Post by Parama on 2011-02-21
Ouch, yes please. Som focus on this matter would be good. It would actually be nice if the iSCSI-SCST would replace the IET packages in the main repo.

I just made a Ubuntu 10.10 server go offline in our co-lo :-(

I was messing around with the iSCSI-SCST setup from [https://wiki.ubuntu.com/scst/]("https://wiki.ubuntu.com/scst/") and had the linux-scst kernel running, the modules loaded and was working on the LV's for the various iSCSI targets.

The iSCSI services had some problems, dropping errors like ```
iscsi-scst: ***ERROR***: Incorrect version of user space 2.0.0.1-rc1_2.0.0.1-...
``` (I can't remember the rest of it) 

Actually, I had the IET iSCSI target running just fine, but convinced myself that iSCSI-SCST was a better solution for our production environment (migrating from Openfiler with just a couple of low I/O targets).

---

### Post by zdali on 2011-03-10
I worked around this problem un 10.04 by downloading the source from the PPA and building manually with following changes:

1) In include/iscsi_scst_ver.h uncomment #define CONFIG_SCST_PROC

2) In include/iscsi_scst_itf_ver.h change 
```
2.0.0.1-rc1-procfs_57aaf159ef6c60783eff3839e56458b060ca741d 
```
to
```
57aaf159ef6c60783eff3839e56458b060ca741d
```

then
```
# make all install
```

I suspect ProcFS version string in 10.10 will be different, but the principle should be the same

HTH

---

### Post by creamecake on 2011-12-21
> **zdali said:**
> I worked around this problem un 10.04 by downloading the source from the PPA and building manually with following changes:

1) In include/iscsi_scst_ver.h uncomment #define CONFIG_SCST_PROC

2) In include/iscsi_scst_itf_ver.h change 
```
2.0.0.1-rc1-procfs_57aaf159ef6c60783eff3839e56458b060ca741d 
```to
```
57aaf159ef6c60783eff3839e56458b060ca741d
```then
```
# make all install
```I suspect ProcFS version string in 10.10 will be different, but the principle should be the same

HTH


When i tried to configure the iscsi-scst, when i started the daemon 
/etc/init.d/iscsi-scst start

it is not actually starting and getting the following error in /var/log/messages
iscsi-scst: ***ERROR***: Incorrect version of user space 2.0.0.1-rc1_2.0.0.1-rc1-procfs_57aaf159ef6c60783eff3839e5645 (expected 2.0.0.1-rc1-procfs_57aaf159ef6c60783eff3839e56458b060ca741d)

then i came across your post and tried to do what u said. for that i installed the following kernel headers 
linux-headers-scst_2.6.32.29.57_amd64.deb

but unable to findout the files which you mentioned,

pls note that i installed the linux-scst as well as the iscsi-scst packages from the repo (i mean as binary, not a compiled one from my system)


more info;
root@ubuntutarget:~# uname -a
Linux ubuntutarget 2.6.32-29-server #57-Ubuntu SMP Mon Jan 31 14:52:04 UTC 2011 x86_64 GNU/Linux
root@ubuntutarget:~# 

root@ubuntutarget:~# aptitude show iscsi-scst
Package: iscsi-scst
New: yes
State: installed
Automatically installed: no
Version: 2.0.0.1-1~ppa3
Priority: extra
Section: devel
Maintainer: Adrian Stachowski <ast@marum.de>
Uncompressed Size: 197k
Depends: libc6 (>= 2.4)
Description: Userspace tools for iSCSI-SCST
 

root@ubuntutarget:~# 

root@ubuntutarget:~# aptitude show scstadmin
Package: scstadmin
New: yes
State: installed
Automatically installed: no
Version: 2.0.0.1-1~ppa1
Priority: extra
Section: devel
Maintainer: Adrian Stachowski <ast@marum.de>
Uncompressed Size: 242k
Description: Admim tool for SCST
 

root@ubuntutarget:~# 

root@ubuntutarget:~# aptitude show linux-scst
Package: linux-scst
New: yes
State: installed
Automatically installed: no
Version: 2.6.32.29.57
Priority: optional
Section: metapackages
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 32.8k
Depends: linux-image-scst (= 2.6.32.29.57)
Description: Complete Linux kernel for scst machines
 This package will always depend on the latest complete Linux kernel available for SCST machines.

root@ubuntutarget:~# aptitude show linux-headers-scst
Package: linux-headers-scst
New: yes
State: installed
Automatically installed: no
Version: 2.6.32.29.57
Priority: optional
Section: devel
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 32.8k
Depends: linux-headers-2.6.32-29-server | linux-headers-2.6.32-29-generic-pae
Description: Linux kernel headers for scst machines
 This package will always depend on the latest kernel headers available for SCST machines (which are the same headers as for the server flavour).



kindly advice me to proceed further....:(

---

