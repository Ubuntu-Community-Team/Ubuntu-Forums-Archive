---
title: "KVM - Host folder does not mount on boot after upgrading guest to Ubuntu 22.04"
date: 2023-05-22
forum: Virtualisation
---

### Post by drumboog on 2023-05-22
Hi,

I have a host machine running Ubuntu 22.04.  It is running KVM and the guest machine was recently upgraded from 20.04 to 22.04.  After the update, the guest machine fails to boot correctly and goes into emergency mode and show and error "Failed to mount /mnt/data".  /mnt/data is mapped from a folder on the host machine and was working prior to the upgrade to 22.04.

If I manually mount the folder with this command, then I can access the files:
mount -t 9p -o trans=virtio /data data/

However, if I reboot, then I get the error again and enter emergency mode.  I have verified that /etc/fstab contains the following line:
/data /mnt/data 9p trans=virtio,version=9p2000.L,rw 0 0

Any help understanding why the mount is failing on boot would be greatly appreciated.

Thank you!

---

### Post by MAFoElffen on 2023-05-23
Add these modules to load at boot time by adding them to the VM file /etc/modules
```

9p
9pnet
9pnet_virtio

```
Then:
```

sudo update-initramfs -u

```

---

### Post by drumboog on 2023-05-23
Thanks, I added those lines and ran the command.  Now, when booting, I receive this error prior to "Failed to mount /mnt/data":
> 9pnet_virtio: no channels available for device /data

---

### Post by MAFoElffen on 2023-05-24
Oh dang... 

I looked it up, and should have been rather added to file /etc/initramfs-tools/modules and included module 'virtio_input'...

---

### Post by drumboog on 2023-05-24
I removed the lines from /etc/modules (it is now empty), and added this to /etc/initramfs-tools/modules:

```

9p
9pnet
9pnet_virtio
virtio_input

```

Then ran:
```
[COLOR=#000000][FONT=&amp]sudo update-initramfs -u[/FONT][/COLOR]
```

I still see this error:
> 9pnet_virtio: no channels available for device /data

---

### Post by MAFoElffen on 2023-05-24
> **drumboog said:**
> However, if I reboot, then I get the error again and enter emergency mode.  I have verified that /etc/fstab contains the following line:
```

/data /mnt/data 9p trans=virtio,version=9p2000.L,rw 0 0

```


Since 2020, people have made this work better, by adding "_netdev" to the end of their fstab line, similar to this (from a user who was having problems with this)
```

/data   /data   9p  trans=virtio,rw,_netdev 0   0

```
Previously, it would not mount if in fstab, but would mount after boot the boot on 'mount -a' to remount the fstab entries. The reason it then worked with this entry, is that it delays the mount until after the networking is up, not because it depends on that, but rather that it gives time for the required kernel modules to be fully loaded.

Try that and see it that works for you.

---

### Post by drumboog on 2023-05-24
It is now booting to the normal terminal instead of emergency mode, but it does not mount the drive.  When I check:
```
journalctl -xb
```
the same errors are there, but have moved later in the log (after the network configuration section).

---

### Post by MAFoElffen on 2023-05-24
...and you said it mounts successfully if you mount it manually (after the boot) with those same options?

---

### Post by drumboog on 2023-05-24
When I originally discovered the issue, I was able to mount after booting with this command:
```
sudo mount -t 9p -o trans=virtio /data data/
```

I believe my playing around with Virtual Machine Manager may have mucked some things up, because it stopped working at some point, but have been able to get it all working now.

Thank you for all the help, MAFoElffen.  I really appreciate it!

For others who may find it helpful, I followed this post to verify my configuration within VMM:
[https://sysguides.com/share-files-between-kvm-host-and-linux-guest-using-virtiofs/](https://sysguides.com/share-files-between-kvm-host-and-linux-guest-using-virtiofs/)

After re-configuring the Filesystem entry in VMM, I was able to manually mount within the guest with this command:
```

sudo mount -t virtiofs /data /mnt/data

```

And I was able to mount at boot by adding this to /etc/fstab:
```

/data   /mnt/data    virtiofs    defaults    0    0

```

---

