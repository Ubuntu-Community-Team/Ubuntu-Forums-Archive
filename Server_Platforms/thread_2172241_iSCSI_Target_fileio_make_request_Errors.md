---
title: "iSCSI Target: fileio_make_request Errors"
date: 2013-09-03
forum: Server Platforms
---

### Post by Kirk Schnable on 2013-09-03
I'm trying to set up my Ubuntu 12.04 file server as an iSCSI target to use with my VMWare ESXi VM server.  I started out by following [this tutorial]("http://qare.org/2012/05/14/ubuntu-12-04-with-iscsi-target-for-vmware-esxi-4-1/"), and other than what I remember from being present while an iSCSI SAN was set up on an ESXi server at work 3 years ago, I don't know much about iSCSI.  This is my first time ever setting it up on Ubuntu, so please don't rule out a foolish mistake having been made.

When I am trying to use the LUN in VMWare, it's pretending like it doesn't exist at times. When I attach\mount the LUN in VMware, I am seeing an error in my syslog on the Ubuntu server.

I'm not 100% sure if this is a Ubuntu\ISCSITarget problem or a VMWare ESXi problem.  Any assistance or advice would be much appreciated.

This is what I'm seeing.

```
Sep  3 20:32:39 ServerHostname kernel: [77541.007006] iSCSI Enterprise Target Software - version 1.4.20.3Sep  3 20:32:39 ServerHostname kernel: [77541.007041] iscsi_trgt: Registered io type fileio
Sep  3 20:32:39 ServerHostname kernel: [77541.007043] iscsi_trgt: Registered io type blockio
Sep  3 20:32:39 ServerHostname kernel: [77541.007044] iscsi_trgt: Registered io type nullio
Sep  3 20:32:46 ServerHostname kernel: [77548.182130] iscsi_trgt: fileio_make_request(63) I/O error 512, 0
Sep  3 20:32:46 ServerHostname kernel: [77548.316244] iscsi_trgt: fileio_make_request(63) I/O error 512, 0
Sep  3 20:32:55 ServerHostname kernel: [77557.134234] iscsi_trgt: fileio_make_request(63) I/O error 512, 0
```

I **do not believe there are genuine I\O problems** as this is all very new hardware.  I've tried using files on my hardware RAID, as well as on my root filesystem which is a single Samsung SSD.

I have tried all 3 of these LUNs, and seem to be experiencing the same problems with all of them.  The files do exist, and are chmodded 777 right now because I wanted to be very sure it was not a permissions issue.  The files are empty (created by *touch* command).

```
TARGET myserverhost.mydomain.com:esxivm
Lun 0 Path=/raid/iscsi/esxivm.iscsi,Type=fileio
Alias VMDatastore


TARGET myserverhost.mydomain.com:esxibk
Lun 1 Path=/raid/iscsi/esxibk.iscsi,Type=fileio
Alias Backups


TARGET myserverhost.mydomain.com:test
Lun 3 Path=/test.iscsi,Type=fileio
Alias Test
```

Let me know if there's anything else you'd like to see from my servers to help with this request.

Here's some basic information about my server:
```
root@ServerHostname:/# lsb_release -aNo LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise
root@ServerHostname:/# uname -r
3.8.0-29-generic
root@ServerHostname:/# dpkg --list | grep iscsi
ii  iscsitarget                      1.4.20.2-5ubuntu3.3          iSCSI Enterprise Target userland tools
ii  iscsitarget-dkms                 1.4.20.2-5ubuntu3.3          iSCSI Enterprise Target kernel module source - dkms version
ii  open-iscsi                       2.0.871-0ubuntu9.12.04.2     High performance, transport independent iSCSI implementation
ii  open-iscsi-utils                 2.0.871-0ubuntu9.12.04.2     iSCSI initiatior administrative utility
root@ServerHostname:/# 
```

Thanks,
Kirk

---

### Post by stokkeland on 2013-11-22
Did you ever figure this out?

I am about to embark on the same path - I havent seen those errors yet - but I am just curious to what its all about, if there will be some funny issues when I start vMotion and such..  perhaps if there is something other then IET i should use for ubuntu 12.04

---

