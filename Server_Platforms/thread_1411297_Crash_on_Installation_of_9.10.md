---
title: "Crash on Installation of 9.10"
date: 2010-02-19
forum: Server Platforms
---

### Post by douglasj on 2010-02-19
Asus p7f-x mobo
Intel i5 CPU 750
Install to 500g SATA WD drive
4 other 1.5TB WD SATA drives present but not touched during installation
eth0 active and given ip over dhcp

install from USB drive (4g 'cruzer'); successfully installed other systems from this usb drive

During installation random packages report not being able to install during step "Install the base system"

Checking syslog shows that python? is crashing.

```

Feb 19 23:45:26 debootstrap: Processing triggers for initramfs-tools ...
Feb 19 23:45:27 debootstrap: Errors were encountered while processing:
Feb 19 23:45:27 debootstrap:  lsb-release
Feb 19 23:45:27 debootstrap:  ubuntu-minimal
Feb 19 23:45:28 debootstrap: Setting up lsb-release (4.0-0ubuntu5) ...
Feb 19 23:45:28 debootstrap: Segmentation fault
Feb 19 23:45:28 debootstrap: dpkg: error processing lsb-release (--configure):
Feb 19 23:45:28 debootstrap:  subprocess installed post-installation script returned error exit status 139
Feb 19 23:45:28 debootstrap: dpkg: dependency problems prevent configuration of ubuntu-minimal:
Feb 19 23:45:28 debootstrap:  ubuntu-minimal depends on lsb-release; however:
Feb 19 23:45:28 debootstrap:   Package lsb-release is not configured yet.
Feb 19 23:45:28 debootstrap: dpkg: error processing ubuntu-minimal (--configure):
Feb 19 23:45:28 debootstrap:  dependency problems - leaving unconfigured
Feb 19 23:45:28 kernel: [  251.343567] pycentral[28553]: segfault at 5b ip 08091dc2 sp bfb7bab0 error 4 in python2.6[8048000+1d3000]
Feb 19 23:45:28 debootstrap: Errors were encountered while processing:
Feb 19 23:45:28 debootstrap:  lsb-release
Feb 19 23:45:28 debootstrap:  ubuntu-minimal
Feb 19 23:45:29 debootstrap: Setting up lsb-release (4.0-0ubuntu5) ...
Feb 19 23:45:29 debootstrap: Segmentation fault
Feb 19 23:45:29 debootstrap: dpkg: error processing lsb-release (--configure):
Feb 19 23:45:29 debootstrap:  subprocess installed post-installation script returned error exit status 139
Feb 19 23:45:29 debootstrap: dpkg: dependency problems prevent configuration of ubuntu-minimal:
Feb 19 23:45:29 debootstrap:  ubuntu-minimal depends on lsb-release; however:
Feb 19 23:45:29 debootstrap:   Package lsb-release is not configured yet.
Feb 19 23:45:29 debootstrap: dpkg: error processing ubuntu-minimal (--configure):
Feb 19 23:45:29 debootstrap:  dependency problems - leaving unconfigured
Feb 19 23:45:29 kernel: [  252.525013] pycentral[28563]: segfault at 5b ip 08091dc2 sp bf9c1a60 error 4 in python2.6[8048000+1d3000]
Feb 19 23:45:29 debootstrap: Errors were encountered while processing:
Feb 19 23:45:29 debootstrap:  lsb-release
Feb 19 23:45:29 debootstrap:  ubuntu-minimal
Feb 19 23:45:30 debootstrap: Setting up lsb-release (4.0-0ubuntu5) ...
Feb 19 23:45:30 debootstrap: Segmentation fault
Feb 19 23:45:30 debootstrap: dpkg: error processing lsb-release (--configure):
Feb 19 23:45:30 debootstrap:  subprocess installed post-installation script returned error exit status 139
Feb 19 23:45:30 debootstrap: dpkg: dependency problems prevent configuration of ubuntu-minimal:
Feb 19 23:45:30 debootstrap:  ubuntu-minimal depends on lsb-release; however:
Feb 19 23:45:30 debootstrap:   Package lsb-release is not configured yet.
Feb 19 23:45:30 debootstrap: dpkg: error processing ubuntu-minimal (--configure):
Feb 19 23:45:30 debootstrap:  dependency problems - leaving unconfigured
Feb 19 23:45:30 kernel: [  253.639769] pycentral[28573]: segfault at 5b ip 08091dc2 sp bfdee2b0 error 4 in python2.6[8048000+1d3000]
Feb 19 23:45:30 debootstrap: Errors were encountered while processing:
Feb 19 23:45:30 debootstrap:  lsb-release
Feb 19 23:45:30 debootstrap:  ubuntu-minimal
eb 19 23:45:31 debootstrap: Setting up lsb-release (4.0-0ubuntu5) ...
Feb 19 23:45:31 debootstrap: Segmentation fault
Feb 19 23:45:31 debootstrap: dpkg: error processing lsb-release (--configure):
Feb 19 23:45:31 debootstrap:  subprocess installed post-installation script returned error exit status 139
Feb 19 23:45:31 debootstrap: dpkg: dependency problems prevent configuration of ubuntu-minimal:
Feb 19 23:45:31 debootstrap:  ubuntu-minimal depends on lsb-release; however:
Feb 19 23:45:31 debootstrap:   Package lsb-release is not configured yet.
Feb 19 23:45:31 debootstrap: dpkg: error processing ubuntu-minimal (--configure):
Feb 19 23:45:31 debootstrap:  dependency problems - leaving unconfigured
Feb 19 23:45:31 kernel: [  254.754634] pycentral[28583]: segfault at 5b ip 08091dc2 sp bfbe33d0 error 4 in python2.6[8048000+1d3000]
Feb 19 23:45:31 debootstrap: Errors were encountered while processing:
Feb 19 23:45:31 debootstrap:  lsb-release
Feb 19 23:45:31 debootstrap:  ubuntu-minimal
Feb 19 23:46:17 in-target: Reading package lists...
Feb 19 23:46:17 in-target: Building dependency tree...
Feb 19 23:46:17 in-target: locales is already the newest version.
Feb 19 23:46:17 in-target: 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Feb 19 23:46:17 in-target: 2 not fully installed or removed.
Feb 19 23:46:17 in-target: After this operation, 0B of additional disk space will be used.
Feb 19 23:46:17 in-target: Setting up lsb-release (4.0-0ubuntu5) ...
Feb 19 23:46:17 in-target: Segmentation fault
Feb 19 23:46:17 in-target: dpkg: error processing lsb-release (--configure):
Feb 19 23:46:17 in-target:  subprocess installed post-installation script returned error exit status 139
Feb 19 23:46:17 in-target: dpkg: dependency problems prevent configuration of ubuntu-minimal:
Feb 19 23:46:17 in-target:  ubuntu-minimal depends on lsb-release; however:
Feb 19 23:46:17 in-target:   Package lsb-release is not configured yet.
Feb 19 23:46:17 in-target: dpkg: error processing ubuntu-minimal (--configure):
Feb 19 23:46:17 in-target:  dependency problems - leaving unconfigured
Feb 19 23:46:17 in-target: No apport report written because the error message indicates its a followup error from a previous failure.
Feb 19 23:46:17 kernel: [  300.667200] pycentral[28727]: segfault at 5b ip 08091dc2 sp bfb8c790 error 4 in python2.6[8048000+1d3000]
Feb 19 23:46:17 in-target: Errors were encountered while processing:
Feb 19 23:46:17 in-target:  lsb-release
Feb 19 23:46:17 in-target:  ubuntu-minimal
Feb 19 23:46:17 in-target: E: Sub-process /usr/bin/dpkg returned an error code (1)

```I tried multiple times, seems to report Red Screens of Failure (package blah could not install, will try 5 times <continue>) on different packages and finally one of them won't work and the installation fails.

Not sure where to go with this.  Can anyone suggest any next actions?

---

### Post by lidex on 2010-02-19
Can you post syslog?

---

### Post by douglasj on 2010-02-22
Added syslog

---

### Post by douglasj on 2010-02-22
It appears to be solved.

I got a new sandisk cruzer.  I removed the U3 partition this time with u3-tool then recreated the usb boot disk using usb-creator.  No segfaults this time and install went smoothly.

It appears it was either just that usb key or the U3 partition.

---

