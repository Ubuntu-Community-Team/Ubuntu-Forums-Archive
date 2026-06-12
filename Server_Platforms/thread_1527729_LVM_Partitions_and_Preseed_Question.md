---
title: "LVM Partitions and Preseed Question"
date: 2010-07-09
forum: Server Platforms
---

### Post by ruffEdgz on 2010-07-09
I have been playing around with the preseed configuration file and I'm loving it but having some trouble with one part, partitioning with LVM.

When I PXE boot my Ubuntu 10.04 (64bit) Server in a computer is completes it successfully and the partitions are as followed:

sys_vg-slash -- Root
sys_vg-swap -- Swap
sys_vg-home -- Home Directories

When the system starts up for the first time, both sys_vg-slash and sys_vg-home come out to be 10GB (which is what I want) but the sys_vg-swap logical volume comes out to be the rest of the left over HD space (I only ask swap to be 4GB in the preseed). Below is what I am using to get this to work with LVM but I'm just curious if anyone knows why it might be doing this. Just need to toss around some ideas as I think I'm doing this write:

```

###### Start of the partition section of the preseed ######
d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string lvm
d-i partman-lvm/device_remove_lvm boolean true
d-i partman-lvm/device_remove_lvm_span boolean true
d-i partman-auto/purge_lvm_from_device  boolean true
d-i partman-md/device_remove_md boolean true
d-i partman-lvm/confirm boolean true
###### Here is the recipe I use for the custom setup ######
d-i partman-auto/expert_recipe string                         \
      boot-root ::                                            \
              1024 1024 2048 ext3                             \
                      $primary{ } $bootable{ }                \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext3 }    \
                      mountpoint{ /boot }                     \
              .                                               \
              5000 10000 1000000000 ext3                      \
                      $defaultignore{ }                       \
                      method{ lvm } device{ /dev/sda }        \
                      vg_name{ sys_vg }                       \
              .                                               \
              10000 10000 10000 ext3                          \
                      $lvmok{ } in_vg{ sys_vg }               \
                      lv_name{ slash } method{ format }       \
                      format{ } use_filesystem{ }             \
                      filesystem{ ext3 } mountpoint{ / }      \
              .                                               \
              10000 10000 10000 ext3                          \
                      $lvmok{ } in_vg{ sys_vg }               \
                      lv_name{ home } method{ format }        \
                      format{ } use_filesystem{ }             \
                      filesystem{ ext3 } mountpoint{ /home }  \
              .                                               \
              4000 4000 4000 linux-swap                       \
                      $lvmok{ } in_vg{ sys_vg }               \
                      lv_name{ swap }                         \
                      method{ swap } format{ }                \
              .                                               \

```

I think it has something to do with the creation of the volume group (the second entry in the recipe) but don't know why it would be it though (just have a hunch). Thanks for any help.

---

### Post by lvmhelp on 2010-08-14
you might try to give your other partitions appropriate priorities for example 11000 (10000 11000 10000 ext3) for root, 20000 (10000 20000 10000 ext3) for home directories, and 15000(4000 15000 4000 linux-swap) for swap. Thereby swap will appear just after the root partition and before home directories. In your case all the remaining space was given to swap because it was in the end of lvm volume group.  If the same will now happen with the home directories it would indicate that you should explicitly limit the volume group size to the sum of all logical volume sizes if you would like to keep the remaining disk space free. good luck!

---

