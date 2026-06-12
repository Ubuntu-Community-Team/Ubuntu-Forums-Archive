---
title: "[SOLVED] How do you mount an usb disk in command-line system?"
date: 2008-11-27
forum: Server Platforms
---

### Post by jis on 2008-11-27
My system tells 
> [ numbers:morenumbers] sd number:0:0:0: [sdb] Assuming drive cache: write through
[ numbers:differentmorenumbers] sd number:0:0:0: [sdb] Assuming drive cache: write through

after I plug in a USB stick.

---

### Post by obg123 on 2008-11-27
It gets assigned a /dev/sd? device id. Just have a look right after your regular disks and cd/dvds, and you shall find it.

Maybe it even gets auto mounted. Have a look under /media and see if you don't find it there. Also check the output from mount.

---

### Post by jis on 2008-11-27
I suppose it is /dev/sdb in this case. 

I installed command-line system by this:
[http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/mini.iso)
It does not automount a USB disk so no such item in /media.
If I make a directory mountpoint for it in /media and run "sudo mount /dev/sdb1 /media/mountpoint", I get it mounted :)

---

### Post by prshah on 2008-11-27
> **jis said:**
> 
It does not automount a USB disk so no such item in /media.
If I make a directory mountpoint for it in /media and run "sudo mount /dev/sdb1 /media/mountpoint", I get it mounted

...but with only root permissions. 

You should instead use ```
sudo gnome-mount /dev/sdb
``` which will create a suitable directory in /media/, and mount the drive with proper permissions, and display it in "Computer" along with suitable mount / eject options.

Also, are you sure it's /dev/sdb? That's unusual, it should be /dev/sdb1 or so.

---

### Post by jis on 2008-11-27
Device is /dev/sdb and partition to mount is /dev/sdb1. I doubt gnome-mount is installed in the system by default but it can be installed.

---

### Post by jis on 2008-11-27
```
sudo gnome-mount --device /dev/sdb1
``` creates directory "/media/USB DISK" and uses it as mount point but I can't cd to it.

---

### Post by prshah on 2008-11-27
> **jis said:**
> ```
sudo gnome-mount --device /dev/sdb1
``` creates directory "/media/USB DISK" and uses it as mount point but I can't cd to it.

Try placing the entire path in quotes or escaping the space character```
cd "/media/USB DISK"
cd /media/USB\ DISK

```

---

### Post by jis on 2008-11-27
It does not help: Permission denied. For some reason, I can't change its permissions. Sudo chown does not complain anything, but the permissions are not changed.

---

### Post by prshah on 2008-11-27
> **jis said:**
> It does not help: Permission denied. 

What are the mount directory group, ownership and permissions?```
ls -ld /media
```

It should have owner as root, group as plugdev, and you should be a member of the group plugdev```
groups
```

Make sure you have no entries for /dev/sdb1 in /etc/fstab.

---

### Post by jis on 2008-11-27
/media has owner and group root, same for "/media/USB DISK". But if I use the gnome-mount command as normal user, the latter has the normal user as owner and root as group. Then I can cd to the directory.

Would it be possible to make mounting process automatic?

---

