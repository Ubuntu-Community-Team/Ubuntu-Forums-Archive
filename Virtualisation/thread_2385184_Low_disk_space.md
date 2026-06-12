---
title: "Low disk space"
date: 2018-02-17
forum: Virtualisation
---

### Post by satimis on 2018-02-17
VirtualBox
VM Ubuntu 16.04

&#10219; lsb_release -a```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.3 LTS
Release:        16.04
Codename:       xenial

```

Low disk space warning popup```

The volume filesystem root has onlyh 378.2 MB disk space remaining
.....

```
Please refers to file low_disk_space.png upload

&#10219; free -m```

              total        used        free      shared  buff/cache   available
Mem:           3951         600        2747          19         603        3096
Swap:          2043           0        2043

```

&#10219; sudo blkid```

/dev/sda1: UUID="dfab862e-1205-479e-a522-c56e16c35eeb" TYPE="ext2" PTTYPE="dos" PARTUUID="4b20aaab-01"
/dev/sda5: UUID="00AxDu-cVgJ-1kVJ-LorW-d71L-brOu-rcu369" TYPE="LVM2_member" PARTUUID="4b20aaab-05"
/dev/mapper/ubuntu--vg-root: UUID="5b5180f2-9c7f-4c0a-934d-52f59dcd32e4" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="0feda020-c56b-4009-a272-0369b68e9093" TYPE="swap"

```

&#10219; cat /etc/fstab```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=dfab862e-1205-479e-a522-c56e16c35eeb /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0

```

Please advise how to fix the problem?

Thanks

Regards
satimis

---

### Post by mikewhatever on 2018-02-17
You need to remove stuff from the root partition. 
Check for installed kernels and headers:

```

dpkg -l | grep linux-image
dpkg -l | grep linux-headers

```
Also, remove cached installation packages with <sudo apt-get clean>.

---

### Post by deadflowr on 2018-02-17
```
df -h
```
would also help.

Also is this within the vm or the host?
And how much has been allocated to the vm(s)?

---

### Post by satimis on 2018-02-19
Hi all,

Thanks for your advice.

Sorry I already deleted this VM and recreated a new VM to replace it.  I wouldn't continue this thread.

Regards
satimis

---

