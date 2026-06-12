---
title: "sudo update-initramfs -u -k all going crazy"
date: 2019-03-05
forum: Server Platforms
---

### Post by sexyuser on 2019-03-05
What is this? I mistyped once (..-k all$) and now its coming all the time I using this command

+ how can I remove that [COLOR=#DDDDDD]4.4.0-101-generic

[/COLOR]Thanks & Greetings to the community

```
# sudo update-initramfs -u -k all
update-initramfs: Generating /boot/initrd.img-all$
WARNING: missing /lib/modules/all$
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: Bad version passed all$
dpkg: warning: version 'all$' has bad syntax: version number does not start with a digit
dpkg: warning: version 'all$' has bad syntax: version number does not start with a digit
dpkg: warning: version 'all$' has bad syntax: version number does not start with a digit
dpkg: warning: version 'all$' has bad syntax: version number does not start with a digit
depmod: ERROR: Bad version passed all$
update-initramfs: Generating /boot/initrd.img-4.18.0-15-generic
update-initramfs: Generating /boot/initrd.img-4.15.0-46-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-101-generic
WARNING: missing /lib/modules/4.4.0-101-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-101-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_wDJhK5/lib/modules/4.4.0-101-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_wDJhK5/lib/modules/4.4.0-101-generic/modules.builtin: No such file or directory
update-initramfs: Generating /boot/initrd.img-4.4.0-101
WARNING: missing /lib/modules/4.4.0-101
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-101: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_hM0tmd/lib/modules/4.4.0-101/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_hM0tmd/lib/modules/4.4.0-101/modules.builtin: No such file or directory
```

---

### Post by deadflowr on 2019-03-05
Looks like a leftover kernel from an earlier release.
See if you can just remove the 4.4 kernel.

---

