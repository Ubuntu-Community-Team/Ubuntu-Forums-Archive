---
title: "ZFS: &quot;zpool upgrade -a&quot; does not work"
date: 2018-01-26
forum: Ubuntu Development Version
---

### Post by w00sterf1 on 2018-01-26
I have 2 ZFS pools in a virtualbox environment. When checking their status, I'm told the features needs to be upgraded. I have done this before without any issues but not now. Updated the system today to the latest available packages.  
  
This is what I have:  
  
```

root@Jeeves:~# uname -a
Linux Jeeves 4.13.0-30-generic #33-Ubuntu SMP Mon Jan 15 19:45:48 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
root@Jeeves:~# zpool status
  pool: home
 state: ONLINE
status: Some supported features are not enabled on the pool. The pool can
    still be used, but some features are unavailable.
action: Enable all features using 'zpool upgrade'. Once this is done,
    the pool may no longer be accessible by software that does not support
    the features. See zpool-features(5) for details.
  scan: none requested
config:


    NAME                               STATE     READ WRITE CKSUM
    home                               ONLINE       0     0     0
      raidz3-0                         ONLINE       0     0     0
        pci-0000:00:14.0-scsi-0:0:0:0  ONLINE       0     0     0
        pci-0000:00:14.0-scsi-0:0:1:0  ONLINE       0     0     0
        pci-0000:00:14.0-scsi-0:0:2:0  ONLINE       0     0     0
        pci-0000:00:14.0-scsi-0:0:3:0  ONLINE       0     0     0
        pci-0000:00:14.0-scsi-0:0:4:0  ONLINE       0     0     0
        pci-0000:00:14.0-scsi-0:0:5:0  ONLINE       0     0     0
        pci-0000:00:14.0-scsi-0:0:6:0  ONLINE       0     0     0


errors: No known data errors


  pool: rpool
 state: ONLINE
status: Some supported features are not enabled on the pool. The pool can
    still be used, but some features are unavailable.
action: Enable all features using 'zpool upgrade'. Once this is done,
    the pool may no longer be accessible by software that does not support
    the features. See zpool-features(5) for details.
  scan: none requested
config:


    NAME                                             STATE     READ WRITE CKSUM
    rpool                                            ONLINE       0     0     0
      mirror-0                                       ONLINE       0     0     0
        ata-VBOX_HARDDISK_VB1d2e58b1-5c84c149-part1  ONLINE       0     0     0
        ata-VBOX_HARDDISK_VB5f85de5f-5d20b5cf-part1  ONLINE       0     0     0


errors: No known data errors
root@Jeeves:~# zpool upgrade -a
This system supports ZFS pool feature flags.


cannot set property for 'home': invalid argument for this pool operation

```

I have tried to upgrade the pools manually, one by one:  
```

root@Jeeves:~# zpool upgrade home
This system supports ZFS pool feature flags.


cannot set property for 'home': invalid argument for this pool operation
root@Jeeves:~# zpool upgrade rpool
This system supports ZFS pool feature flags.


cannot set property for 'rpool': invalid argument for this pool operation

```

Since I never gave any argument, the syntax is correct and the zpool program is not letting me know what argument is invalid, it is really difficult to troubleshoot.

I then tried to activate the individual features:
```

root@Jeeves:~# zpool get all rpool
NAME   PROPERTY                       VALUE                          SOURCE
...


rpool  feature@async_destroy          enabled                        local
rpool  feature@empty_bpobj            active                         local
rpool  feature@lz4_compress           active                         local
rpool  feature@multi_vdev_crash_dump  disabled                       local
rpool  feature@spacemap_histogram     active                         local
rpool  feature@enabled_txg            active                         local
rpool  feature@hole_birth             active                         local
rpool  feature@extensible_dataset     enabled                        local
rpool  feature@embedded_data          active                         local
rpool  feature@bookmarks              enabled                        local
rpool  feature@filesystem_limits      enabled                        local
rpool  feature@large_blocks           enabled                        local
rpool  feature@large_dnode            disabled                       local
rpool  feature@sha512                 disabled                       local
rpool  feature@skein                  disabled                       local
rpool  feature@edonr                  disabled                       local
rpool  feature@userobj_accounting     disabled                       local
root@Jeeves:~# zpool set feature@large_dnode=enabled rpool
cannot set property for 'rpool': invalid argument for this pool operation
root@Jeeves:~# zpool set feature@sha512=enabled rpool
cannot set property for 'rpool': invalid argument for this pool operation
root@Jeeves:~# zpool set feature@skein=enabled rpool
cannot set property for 'rpool': invalid argument for this pool operation
root@Jeeves:~# zpool set feature@edonr=enabled rpool
cannot set property for 'rpool': invalid argument for this pool operation
root@Jeeves:~# zpool set feature@userobj_accounting=enabled rpool
cannot set property for 'rpool': invalid argument for this pool operation

```


Anyone else seen this before?

I also tried to scrub both volumes but that changed nothing.

---

### Post by slickymaster on 2018-01-27
Thread moved to **Virtualisation** for a better fit

---

### Post by w00sterf1 on 2018-01-27
Ok, but it is in 18.04 and has nothing to do with the virtualization.  
  
It simply seems that the updates of Bionic's ZFS programs do not correctly compile in the correct version of the ZFS tools and do not build a correct initramfs. I worked around it by install zfs-dkms and now I have been able to upgrade the ZFS filesystems. Took me a while to debug the issue.

---

### Post by slickymaster on 2018-01-29
> **w00sterf1 said:**
> Ok, but it is in 18.04 and has nothing to do with the virtualization.  
  
It simply seems that the updates of Bionic's ZFS programs do not correctly compile in the correct version of the ZFS tools and do not build a correct initramfs. I worked around it by install zfs-dkms and now I have been able to upgrade the ZFS filesystems. Took me a while to debug the issue.

Being so, moved to the **Ubuntu Development Version** forum

---

