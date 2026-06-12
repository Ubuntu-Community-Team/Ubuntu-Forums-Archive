---
title: "Permission Issues With KVM/Virt-Manager"
date: 2014-07-19
forum: Virtualisation
---

### Post by rayj00 on 2014-07-19
My Host is Ubuntu 14.04 Desktop. New install and updated.

I followed the procedures at [https://help.ubuntu.com/community/KVM/Installation](https://help.ubuntu.com/community/KVM/Installation) for the installation.

I am logged in as "ray".  

When I try to create a VM of Ubuntu 14.04 Server, using virt-manager, I get this:

"The emulator may not have search permissions for the path '/media/ray/HDD 1T/Virtual Machines/Ubuntu14.04Server'.
Do you want to correct this now?"

I answer Yes then get this:

"Errors were encountered changing permissions for the following directories:
/media/ray/HDD 1T/Virtual Machines : Permissions on '/media/ray/HDD 1T/Virtual Machines' did not stick
/media/ray/HDD 1T : Permissions on '/media/ray/HDD 1T' did not stick
/media/ray : [Errno 1] Operation not permitted: '/media/ray'

HDD 1T is a 1Tb disk I use to store the VM images.

I continue and then get this almost immediately:

Unable to complete install: 'internal error: process exited while connecting to monitor: qemu-system-x86_64: -drive file=/media/ray/HDD 1T/Virtual Machines/Ubuntu14.04Server,if=none,id=drive-virtio-disk0,format=raw: could not open disk image /media/ray/HDD 1T/Virtual Machines/Ubuntu14.04Server: Could not open '/media/ray/HDD 1T/Virtual Machines/Ubuntu14.04Server': Permission denied

Ideas?

Thanks,

Ray

---

### Post by TheFu on 2014-07-20
Please post the output from 'id' for the ray account.

---

### Post by fredrik-normann on 2015-01-22
I have the same issue. Here's my output from 'id'

```

fredrik@cartman:/media$ id
uid=1000(fredrik) gid=1000(fredrik) groups=1000(fredrik),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),108(lpadmin),124(sambashare),125(libvirtd)

```

---

### Post by TheFu on 2015-01-22
Are you using a linux file system?
I'm guessing that NTFS, xfat, fat32 are not supported.

---

### Post by fredrik-normann on 2015-01-22
I use ext4

---

### Post by TheFu on 2015-01-22
Please, can you post the relevant libvirtd error logs?

---

