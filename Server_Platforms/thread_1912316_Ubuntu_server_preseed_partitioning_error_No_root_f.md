---
title: "Ubuntu server preseed partitioning error: No root filesystem"
date: 2012-01-20
forum: Server Platforms
---

### Post by ogeen on 2012-01-20
I am trying to perform automatic installation of Ubuntu server (11.10). My partitioning recipe is here:

```


d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string lvm
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-lvm/device_remove_lvm_span boolean true
d-i partman-auto/purge_lvm_from_device boolean true
d-i partman-auto-lvm/new_vg_name string vg00
d-i partman-auto-lvm/guided_size string max
d-i partman/alignment select cylinder
d-i partman-auto/choose_recipe select boot-root
d-i partman-auto/expert_recipe string \
  boot-root ::                    \
    228 8000 256 ext2             \
      $primary{ }                     \
      $bootable{ }                \
      method{ format }            \
      format{ }                       \
      use_filesystem{ }               \
      filesystem{ ext2 }              \
      mountpoint{ /boot } .       \
    100 7000 1000000000 ext4      \
      $primary{ }                     \
      $defaultignore{ }       \
      method{ lvm }           \
      device{ /dev/sda }          \
      vg_name{ vg00 } .               \
    322 5000 1000000000 ext4      \
      $lvmok{ }               \
      in_vg{ vg00 }           \
      lv_name{ root }         \
      method{ format }        \
      format{ }               \
      use_filesystem{ }       \
      filesystem{ ext4 }          \
      mountpoint { / } .              \
    4096 6000 4128 swap       \
      $lvmok{ }               \
      in_vg{ vg00 }           \
      lv_name{ swap }         \
      method{ swap }          \
      format{ } .             \
    1024 4000 1088 ext4           \
      $lvmok{ }               \
      in_vg{ vg00 }           \
      lv_name{ tmp }          \
      method{ format }        \
      format{ }               \
      use_filesystem{ }       \
      filesystem{ ext4 }          \
      mountpoint { /tmp } .       \
    10240 3000 10256 ext4         \
      $lvmok{ }               \
      in_vg{ vg00 }           \
      lv_name{ usr }          \
      method{ format }        \
      format{ }               \
      use_filesystem{ }       \
      filesystem{ ext4 }          \
      mountpoint { /usr } .       \
    5120 2000 5168 ext4           \
      $lvmok{ }               \
      in_vg{ vg00 }           \
      lv_name{ var }          \
      method{ format }        \
      format{ }               \
      use_filesystem{ }       \
      filesystem{ ext4 }          \
      mountpoint { /var } .       \
    153600 1000 1000000000 ext4       \
      $lvmok{ }               \
      in_vg{ vg00 }           \
      lv_name{ home }         \
      method{ format }        \
      format{ }               \
      use_filesystem{ }       \
      filesystem{ ext4 }          \
      mountpoint { /home } .
d-i partman-lvm/confirm boolean true
d-i partman/confirm_write_new_label boolean true
d-i partman/choose_partition select Finish
d-i partman/confirm boolean true
d-i partman/confirm_nooverwrite boolean true



```I always end on error:
  No root file system is defined.
  Please correct this from the partitioning menu.

  [IMG]http://imageshack.us/photo/my-images/526/erroroq.png[/IMG][IMG]http://imageshack.us/photo/my-images/526/erroroq.png[/IMG][http://imageshack.us/photo/my-images/526/erroroq.png](http://imageshack.us/photo/my-images/526/erroroq.png)

  By choosing continue I just receive the same screen again.

  Syslog messages:

```


Jan 20 13:00:02 debconf: --> METAGET partman-lvm/text/in_use description
Jan 20 13:00:02 debconf: <-- 0 In use by LVM volume group vg00
Jan 20 13:00:02 debconf: --> GET partman-auto/method
Jan 20 13:00:02 debconf: <-- 0 lvm
Jan 20 13:00:02 debconf: --> METAGET partman/text/scsi_disk description
Jan 20 13:00:02 debconf: <-- 0 SCSI%s (%s,%s,%s) (%s)
Jan 20 13:00:02 debconf: --> METAGET partman-auto/text/automatically_partition description
Jan 20 13:00:02 debconf: <-- 0 Guided partitioning
Jan 20 13:00:02 debconf: --> METAGET partman-md/text/configure_md description
Jan 20 13:00:02 debconf: <-- 0 Configure software RAID
Jan 20 13:00:02 debconf: --> METAGET partman-lvm/text/configure_lvm description
Jan 20 13:00:02 debconf: <-- 0 Configure the Logical Volume Manager
Jan 20 13:00:02 debconf: --> METAGET partman-crypto/text/configure_crypto description
Jan 20 13:00:02 debconf: <-- 0 Configure encrypted volumes
Jan 20 13:00:02 debconf: --> METAGET partman-iscsi/text/configure_iscsi description
Jan 20 13:00:02 debconf: <-- 0 Configure iSCSI volumes
Jan 20 13:00:03 debconf: --> METAGET partman/text/lvm_lv description
Jan 20 13:00:03 debconf: <-- 0 LVM VG %s, LV %s
Jan 20 13:00:03 debconf: --> METAGET partman/text/lvm_lv description
Jan 20 13:00:03 debconf: <-- 0 LVM VG %s, LV %s
Jan 20 13:00:03 debconf: --> METAGET partman/text/lvm_lv description
Jan 20 13:00:03 debconf: <-- 0 LVM VG %s, LV %s
Jan 20 13:00:03 debconf: --> METAGET partman/text/lvm_lv description
Jan 20 13:00:03 debconf: <-- 0 LVM VG %s, LV %s
Jan 20 13:00:03 debconf: --> METAGET partman/text/lvm_lv description
Jan 20 13:00:03 debconf: <-- 0 LVM VG %s, LV %s
Jan 20 13:00:03 debconf: --> METAGET partman/text/lvm_lv description
Jan 20 13:00:03 debconf: <-- 0 LVM VG %s, LV %s
Jan 20 13:00:03 debconf: --> METAGET partman/text/scsi_disk description
Jan 20 13:00:03 debconf: <-- 0 SCSI%s (%s,%s,%s) (%s)
Jan 20 13:00:03 debconf: --> METAGET partman/text/undo_everything description
Jan 20 13:00:03 debconf: <-- 0 Undo changes to partitions
Jan 20 13:00:03 debconf: --> METAGET partman/text/end_the_partitioning description
Jan 20 13:00:03 debconf: <-- 0 Finish partitioning and write changes to disk
Jan 20 13:00:03 debconf: --> METAGET partman/choose_partition choices-c
Jan 20 13:00:03 debconf: <-- 0 
Jan 20 13:00:03 debconf: --> SET partman/choose_partition 90finish__________finish
Jan 20 13:00:03 debconf: <-- 0 value set
Jan 20 13:00:03 debconf: --> SUBST partman/choose_partition CHOICES 20auto__________auto, 25md__________md, 30lvm__________lvm, 35crypto__________crypto, 40iscsi__________iscsi, 55divider_up__________divider, 60partition_tree__________/var/lib/partman
Jan 20 13:00:03 debconf: Adding [CHOICES] -> [20auto__________auto, 25md__________md, 30lvm__________lvm, 35crypto__________crypto, 40iscsi__________iscsi, 55divider_up__________divider, 60partition_tree__________/var/lib/partman/devices/=dev=mapper=v
Jan 20 13:00:03 debconf: <-- 0
Jan 20 13:00:03 debconf: --> SUBST partman/choose_partition DESCRIPTIONS Guided partitioning, Configure software RAID, Configure the Logical Volume Manager, Configure encrypted volumes, Configure iSCSI volumes, , LVM VG vg00\, LV home - 153.6 GB Linux
Jan 20 13:00:03 debconf: Adding [DESCRIPTIONS] -> [Guided partitioning, Configure software RAID, Configure the Logical Volume Manager, Configure encrypted volumes, Configure iSCSI volumes, , LVM VG vg00\, LV home - 153.6 GB Linux device-mapper (linear
Jan 20 13:00:03 debconf: <-- 0
Jan 20 13:00:03 debconf: --> INPUT critical partman/choose_partition
Jan 20 13:00:03 debconf: <-- 30 question skipped
Jan 20 13:00:03 debconf: --> GO
Jan 20 13:00:03 debconf: <-- 0 ok
Jan 20 13:00:03 debconf: --> GET partman/choose_partition
Jan 20 13:00:03 debconf: <-- 0 90finish__________finish
Jan 20 13:00:03 debconf: --> GET debian-installer/locale
Jan 20 13:00:03 debconf: <-- 0 en_US.UTF-8
Jan 20 13:00:03 debconf: --> CAPB align
Jan 20 13:00:03 debconf: <-- 0 multiselect backup progresscancel align plugin-terminal plugin-detect-keyboard
Jan 20 13:00:03 debconf: --> INPUT critical partman-target/no_root
Jan 20 13:00:03 debconf: <-- 0 question will be asked
Jan 20 13:00:03 debconf: --> GO 



```Volume group and logical volumes are successfully created. I spent almost two days with testing and googling. Now I really dont know what should I try now. Thanks for any help.

---

### Post by ogeen on 2012-01-23
the trouble was in this line:
    
```
mountpoint { / } .              \   
```

It should look like this:
    
```
mountpoint{ / } .              \ 
``` 


 sigh...

---

### Post by LHammonds on 2012-01-23
Ouch.  All that over a single space character?  Dang.

---

