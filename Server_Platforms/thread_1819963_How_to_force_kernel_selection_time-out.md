---
title: "How to force kernel selection time-out"
date: 2011-08-07
forum: Server Platforms
---

### Post by sblandford on 2011-08-07
I have set the kernel selection time out to 3 seconds. However, sometimes it just hangs indefinitely on the kernel selection screen until I manually select the kernel. This is bad news since it is a VM started up from a script and _has_ to start automatically. The VM is a re-constructed cloud backup made by rsync and re-running grub.

Is there any way to force Ubuntu to NEVER, under any circumstances, not time out on kernel selection.

---

### Post by papibe on 2011-08-07
Maybe a timeout of 0 (zero) may work? Take a look at the section 'Boot Options / Appearance' this [tutorial]("https://help.ubuntu.com/community/StartUpManager").

Regards.

---

### Post by sblandford on 2011-08-08
The tutorial is for the GUI tool but I am using only a blackscreen install. Also, the timeout is already set to 2 seconds by setting GRUB_TIMEOUT=2 in /etc/defaut/grub.

The problem is that the timeout is disabled if a previous boot was unsuccessful. Grub records this in the grub environment variable "recordfail".

To ensure the next boot doesn't fail to time out I just run the following command on the chrooted VM filesystem....

```
grub-editenv /boot/grub/grubenv unset recordfail
```

---

