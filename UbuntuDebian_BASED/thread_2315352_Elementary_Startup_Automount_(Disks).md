---
title: "Elementary Startup Automount (Disks)"
date: 2016-02-27
forum: Ubuntu/Debian BASED
---

### Post by obsidian3 on 2016-02-27
Hey, does anyone else have issues with automounting drives in Elementary using Disks?

I installed the gnome-disk-utility and set up all my automount settings to fit my Debian setup but it doesn't work in Elementary for some reason. Fails to automount at boot.

Any suggestions?

My fstab. Am I missing something simple?
```

`# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc11 during installation
UUID=6114fbc7-6e1b-470a-ae32-bacd9eaf477e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdc6 during installation
UUID=d6a58b4b-ca05-438c-a098-a505e7e5eddd none            swap    sw              0       0
/dev/disk/by-uuid/6111059F06AD6AC1 /mnt/windows auto nosuid,nodev,nofail,noauto,x-gvfs-name=Windows 0 0
/dev/disk/by-uuid/fdef702f-fa6c-4bc7-8a86-93aadb6dd708 /mnt/debian auto nosuid,nodev,nofail,noauto,x-gvfs-name=Debian 0 0
/dev/disk/by-uuid/defdb821-d576-4feb-8891-2d5821e41ca5 /mnt/deepin auto nosuid,nodev,nofail,noauto,x-gvfs-name=Deepin 0 0
/dev/disk/by-uuid/2837e742-a022-42e2-8c3b-0c2374262382 /mnt/android auto nosuid,nodev,nofail,noauto,x-gvfs-name=Android 0 0
/dev/disk/by-uuid/d6169501-50d8-4f60-900d-dc58acd47e84 /mnt/software auto nosuid,nodev,nofail,x-gvfs-name=Software 0 0
/dev/disk/by-uuid/db461a83-7a0b-44a8-898e-ee5d70884c90 /mnt/music auto nosuid,nodev,nofail,x-gvfs-name=Music 0 0
/dev/disk/by-uuid/79623efc-e5b1-4a6d-9ecd-1fc56431a32b /mnt/machines auto nosuid,nodev,nofail,x-gvfs-name=Machines 0 0
/dev/disk/by-uuid/a852acbe-e21a-4255-b228-83fa670e6a90 /mnt/video auto nosuid,nodev,nofail,x-gvfs-name=Video 0 0

```

---

