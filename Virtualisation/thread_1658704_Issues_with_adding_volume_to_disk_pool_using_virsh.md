---
title: "Issues with adding volume to disk pool using virsh in kvm"
date: 2011-01-03
forum: Virtualisation
---

### Post by ed64 on 2011-01-03
This is the error I get:
```

root@codis:/etc/libvirt/storage# virsh vol-create-as --pool sde --name 1 --capacity 100M --allocation 100M
error: Failed to create vol 1
error: internal error ' /dev/sde mkpart --script primary ext2 17408B 106928639B' exited with non-zero status 1 and signal 0: libvir: error : cannot execute binary : No such file or directory

```

Seems like PARTED is empty, it should be something like
```

parted /dev/sde mkpart 

```

Instead it's missing. I'm rebuilding from source to see if that helps. strace didn't really reveal much... nothing useful in the syslog debug logs either.

sde is a GPT pool. Similar result using a DOS format pool

Also found in the Maverick build log, parted is not found:

[https://launchpad.net/ubuntu/maverick/+source/libvirt/+builds?build_state=all](https://launchpad.net/ubuntu/maverick/+source/libvirt/+builds?build_state=all)
> 
checking for DEVMAPPER... yes
**checking for parted... no**
checking parted/parted.h usability... yes
checking parted/parted.h presence... yes
checking for parted/parted.h... yes
checking for uuid_generate in -luuid... yes
checking for ped_device_read in -lparted... yes


**Update a few hours later:**
After rebuilding libvirt, virt-manager/virsh and other tools can now create partitions when using disk pools. I'll file a bug with Ubuntu and libvirtd (I'm thinking that the path to parted should really be configurable and not compiled in!) Or at least show a reasonable warning...

---

