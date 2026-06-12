---
title: "Set Quota on a Encrypted LVM Disk"
date: 2012-12-18
forum: Server Platforms
---

### Post by dr1134 on 2012-12-18
I have a folder, /home.ldap, that holds the home folders for remote users. I need to set a quota of about 30 gb for the users that use that folder. My disk is an encrypted LVM disk that, according to fstab, looks like this:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/ulysses-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=0c621cd8-4fcf-4dcf-b2e2-e2623d35cccd /boot           ext2    defaults     $
/dev/mapper/ulysses-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```

None of the tutorials that I looked up correspond to my setup and I am at a complete loss of how to go about this.

---

