---
title: "reattach software raid to clean install"
date: 2013-07-31
forum: Server Platforms
---

### Post by scottie4442 on 2013-07-31
I have a NAS that was running 12.10, I am going to have to do a reinstall of the / drive.  I have a software raid 5 that I created.  I would like to reattach the raid after the install, the / is not on the raid it is /home/media/ .  I know I need to use mdadm but not sure of the command syntax for this.  Also I cannot go to 13.04, I have a rocketraid rr2680 and cannot get it to install under 13.04.

---

### Post by SaturnusDJ on 2013-07-31
After reinstall you install mdadm.

Then scan for arrays and add them to the config:
```
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```
Update initramfs:
```
update-initramfs -u
```

After this and a reboot, a md device is available to mount.
Mount the disk manually, or via a /etc/fstab entry.

---

