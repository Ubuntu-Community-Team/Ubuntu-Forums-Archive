---
title: "Help understanding ZFS on Root support in 24.04 on non-Pop Ubuntu?"
date: 2024-08-16
forum: System76 Support
---

### Post by Surfrock66 on 2024-08-16
I think I misunderstood how well supported ZFS on Root was on Ubuntu 24.04 with the System76 PPA, and I'm wondering if I can get some clarification if this is just my misunderstanding, or if there's something I should be doing differently to make this work.  I'm using generic Ubuntu on a System76 Thelio, so I have the System76 PPA for drivers.

I set up a fresh install with a mirrored ZFS pool on 2 NVME drives.  Everything worked fine.  After some upgrades, the system essentially became unbootable unless I chose the oldest kernel version.  I get dropped to an initramfs with an error "Failed to load ZFS modules" and then have to reboot and choose an older kernel in Grub.

As I understand it, Ubuntu's packaged ZFS version is 2.2.2, which despite being listed as only compatible with kernels 3.10-6.6, is patched to be compatible with the 6.8.0-31 kernel that ships with 24.04.

References: 
[https://github.com/openzfs/zfs/tree/zfs-2.2.2](https://github.com/openzfs/zfs/tree/zfs-2.2.2)
[https://discourse.ubuntu.com/t/introducing-kernel-6-8-for-the-24-04-noble-numbat-release/41958](https://discourse.ubuntu.com/t/introducing-kernel-6-8-for-the-24-04-noble-numbat-release/41958)

At this time though, doing a dist-upgrade got me an upgrade to kernel 6.9 (specifically 6.9.3.76060903.202405300957~1719980995~24.04~fa56f73~dev) which is referenced as the "linux-generic" package.  My understanding is that this is from the system76 kernel repo:

```
root@sr66-thelio:~# apt policy linux-generic
linux-generic:
  Installed: 6.9.3.76060903.202405300957~1719980995~24.04~fa56f73~dev
  Candidate: 6.9.3.76060903.202405300957~1719980995~24.04~fa56f73~dev
  Version table:
 *** 6.9.3.76060903.202405300957~1719980995~24.04~fa56f73~dev 1001
       1001 https://ppa.launchpadcontent.net/system76-dev/stable/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
     6.8.0-40.40 500
        500 http://us.archive.ubuntu.com/ubuntu noble-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu noble-security/main amd64 Packages
     6.8.0-31.31 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
```


Doing this made my system un-bootable; as the listed compatibility for 2.2.2 ends at 6.8.  It seems the zfs-dkms module is incompatible with this kernel version:

```
Building initial module for 6.9.3-76060903-generic
configure: error: 
	*** None of the expected "blkdev_get_by_path()" interfaces were detected.
	*** This may be because your kernel version is newer than what is
	*** supported, or you are using a patched custom kernel with
	*** incompatible modifications.
	***
	*** ZFS Version: zfs-2.2.2-0ubuntu9
	*** Compatible Kernels: 3.10 - 6.6
	
ERROR (dkms apport): kernel package linux-headers-6.9.3-76060903-generic is not supported
Error! Bad return status for module build on kernel: 6.9.3-76060903-generic (x86_64)
Consult /var/lib/dkms/zfs/2.2.2/build/make.log for more information.
dpkg: error processing package zfs-dkms (--configure):
 installed zfs-dkms package post-installation script subprocess returned error exit status 10
```

I see that technically 2.2.5 supports kernel 6.9, but that hasn't landed in Ubuntu yet: [https://github.com/openzfs/zfs/tree/zfs-2.2.5](https://github.com/openzfs/zfs/tree/zfs-2.2.5)

My question is, how can I pin the kernel version to a 6.8* train?  Or, can I say that that package can only be installed from the mainline Ubuntu repos?  Or, was it just a mistake to install ZFS on root on a System76 system?  Are there any plans to maybe support a compatible ZFS dkms module with the version system76 is pushing (I figure that's a long shot)?  Any advice is appreciated; since this has happened I've basically lost the ability to do unattended reboots.

---

### Post by &amp;KyT$0P# on 2024-08-19
To temporarily pin the kernel to an older version:

edit [FONT=monospace]/etc/default/grub[/FONT] as root, change
```
GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
```
to
```
GRUB_DEFAULT=saved
GRUB_SAVEDEFAULT=true
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=5
```

Run [FONT=monospace]sudo update-grub[/FONT] to apply the change.  Then reboot and select the working kernel from the GRUB menu.

To un-pin the kernel, just manually select the default boot entry at the GRUB menu.

As for ZFS not working with System76 kernel, doesn't System76 package [ZFS in their PPA]("https://launchpad.net/~system76-dev/+archive/ubuntu/stable/+packages?field.name_filter=zfs&field.status_filter=published&field.series_filter=") to avoid this problem?

---

### Post by Surfrock66 on 2024-08-19
I'll end up doing that.   Their zfs package isn't in the noble repo, it stops at jammy sadly.

---

### Post by &amp;KyT$0P# on 2024-08-19
> **Surfrock66 said:**
> Their zfs package isn't in the noble repo, it stops at jammy sadly.

Might this be worth reporting [here]("https://github.com/pop-os/zfs-linux/issues")?

---

