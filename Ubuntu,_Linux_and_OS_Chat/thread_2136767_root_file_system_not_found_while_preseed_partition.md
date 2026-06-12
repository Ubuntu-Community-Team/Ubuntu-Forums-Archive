---
title: "root file system not found while preseed partitioning in ubuntu precise 12.04"
date: 2013-04-18
forum: Ubuntu, Linux and OS Chat
---

### Post by rakesh_roshan on 2013-04-18
I am using following partition recipe for my partition on ubuntu 12.04 precise.


    d-i partman-auto/disk string /dev/sda
    d-i partman-auto/method string lvm
    d-i partman-lvm/device_remove_lvm boolean true
    d-i partman-lvm/device_remove_lvm_span boolean true
    d-i partman-auto/purge_lvm_from_device boolean true
    d-i partman-md/device_remove_md boolean true
    d-i partman-lvm/confirm boolean true
    d-i partman-auto/choose_recipe select boot-root
 
    d-i partman-auto/expert_recipe string                         \
      boot-root ::                                            \
              256 500 1024 ext3                                  \
                      $primary{ } $bootable{ }                \
                      method{ format } format{ }              \
                      use_filesystem{ } filesystem{ ext3 }    \
                      mountpoint{ /boot }                     \
              .                                               \
              100 600 100000 ext3                \
                  $defaultignore{ }             \
              method{ lvm } device{ /dev/sda }        \
              vg_name{ system }                \
          .                            \
              512 1024 200% linux-swap                          \
              $lvmok{ }                    \
              in_vg{ system }                \
              lv_name{ swap }                \
                      method{ swap } format{ }                \
              .                                               \
              2000 3000 4000 ext3                       \
              $lvmok{ }                    \
                      mountpoint{ /tmp }                         \
              in_vg{ system }                \
              lv_name{ TEMP }
                      method{ format }               \
                      format{ } use_filesystem{ } filesystem{ ext3 }    \
              .                                               \
              10000 14000 20000 ext3                       \
              $lvmok{ }                    \
              in_vg{ system }                \
                      mountpoint{ / }                         \
              lv_name{ ROOT }                \
                      method{ format }               \
                      format{ } use_filesystem{ } filesystem{ ext3 }    \
              .                                               \
              5000 6000 10000 ext3                       \
              $lvmok{ }                    \
              in_vg{ system }                \
                      mountpoint{ /var }                         \
              lv_name{ VAR }                 \
                      method{ format }               \
                      format{ } use_filesystem{ } filesystem{ ext3 }    \
              .                                               \
              5000 6000 10000 ext3                       \
              $lvmok{ }                    \
              in_vg{ system }                \
                      mountpoint{ /home }                         \
              lv_name{ HOME }                 \
                      method{ format }               \
                      format{ } use_filesystem{ } filesystem{ ext3 }    \
              .                                               \
              10000 15000 100000 ext3                       \
              $lvmok{ }                    \
              in_vg{ system }                \
                      mountpoint{ /usr }                         \
              lv_name{ USR }                 \
                      method{ format }               \
                      format{ } use_filesystem{ } filesystem{ ext3 }    \
              .                                               \

    d-i partman/confirm_write_new_label boolean true
    d-i partman/choose_partition select finish
    d-i partman/confirm boolean true

---

