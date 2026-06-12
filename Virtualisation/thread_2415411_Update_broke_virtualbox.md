---
title: "Update broke virtualbox"
date: 2019-03-25
forum: Virtualisation
---

### Post by lsutiger on 2019-03-25
I know I SHOULD post this to the VirtialBox forum, but take a look at this requirement:
[IMG]https://imgur.com/a/4t3HoQP[/IMG]
I attempted to create an account, but cannot get a confirmation email. On to the post.
OS: Ubuntu 16.04 64bit with Gnome-Classic
I restarted my computer this morning after an update. Now when I attempt to start andy of my VMs in VirtualBox I receive the following error:
```
The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing
'/sbin/vboxconfig'
as root.
where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT. 
```
I run the command via sudo and receive this error:
```
vboxdrv.sh: Stopping VirtualBox services.
vboxdrv.sh: Starting VirtualBox services.
vboxdrv.sh: Building VirtualBox kernel modules.
vboxdrv.sh: failed: Look at /var/log/vbox-setup.log to find out what went wrong.

There were problems setting up VirtualBox.  To re-start the set-up process, run
  /sbin/vboxconfig
as root.

```
I have attached the /var/log/vbox-setup.log file.
[ATTACH]282847[/ATTACH]

I am currently stuck and do not know how to fix this.

---

### Post by slickymaster on 2019-03-25
*Thread moved to **Virtualisation**.*

---

### Post by ajgreeny on 2019-03-25
Try booting to the previous kernel as there is a known problem with one version in the 4.4 series in 16.04.

This was discussed in great detail in the thread at [https://ubuntuforums.org/showthread.php?t=2415046](https://ubuntuforums.org/showthread.php?t=2415046)

---

### Post by lsutiger on 2019-03-25
This worked. Thanks!

---

