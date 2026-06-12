---
title: "lxc containers and do-release-upgrade?"
date: 2011-10-17
forum: Virtualisation
---

### Post by M1chaelk on 2011-10-17
Hi

I upgraded my 11.04 to 11.10 server successfully and now have a bunch of lxc containers still running 11.04.... Any hints how to upgrade them?  "do-release-upgrade" does no seem to work inside the container :(

Any hints?

Thanks in advance

Michael

---

### Post by M1chaelk on 2011-10-18
Managed to solve this myself.... :-)

```
# Stop the container
lxc-stop -n <container_name>


# Mount the filessystems manually
mount -t proc proc -o nodev,noexec,nosuid /var/lib/lxc/<container_name>/rootfs/proc
mount -t sysfs sysfs /var/lib/lxc/<container_name>/rootfs/sys
mount -t devpts devpts /var/lib/lxc/<container_name>/rootfs/dev/pts
 
# Perform the update
chroot /var/lib/lxc/<container_name>/rootfs /usr/bin/do-release-upgrade 
 
# Unmount the filsystems
umount /var/lib/lxc/<container_name>/rootfs/dev/pts
umount /var/lib/lxc/<container_name>/rootfs/sys
umount /var/lib/lxc/<container_name>/rootfs/proc
```Basically you should be able to use lxc-execute but does not seem to work...

---

### Post by skmakine on 2012-03-23
You can successfully do a dist-upgrade or a do-release-upgrade within an 11.04 lxc guest if you first unmount /lib/init/fstab

For anyone doing this, you should either remove any IP address from the lxc config file, or remove the ethernet device from /etc/network/interfaces. Lxc has issues when there is an IP address present in the config file as well as in the interfaces file.

Also using 11.10 inside lxc will not properly create the /run/lock directory on boot. To fix this, install the latest lxcguest package from Oneiric proposed updates.

---

