---
title: "Issue with NFS"
date: 2014-08-22
forum: Server Platforms
---

### Post by chrisguk on 2014-08-22
I have created some NFS mounts from my NAS box to the buntu 14.04 server box.  This is the content of my fstab:

```
nas.me.home:/volume1/Movies     /home/movies                 nfs     rw,noauto  0  0 
```

The problem I am having is, when I create another folder under the mount "/home/movies" the folder does not retain the permission of its parent folder, so it defualts to rw,ro,ro.  Can anyone offer some tips on what to check?

---

### Post by steeldriver on 2014-08-22
I don't think *nix files/directories inherit permissions from their parent, do they? that should be determined by the umask of the creating process (which defaults to 0022 in Ubuntu) - although it's possible to do it via ACLs I think

*Some *filesystems allow setting a umask (and/or separate fmask/dmask) for the volume at mount time - but I think only those that don't support the *nix way of doing it (e.g. ntfs)

---

### Post by bab1 on 2014-08-22
> **steeldriver said:**
> I don't think *nix files/directories inherit permissions from their parent, do they? that should be determined by the umask of the creating process (which defaults to 0022 in Ubuntu) - although it's possible to do it via ACLs I think

*Some *filesystems allow setting a umask (and/or separate fmask/dmask) for the volume at mount time - but I think only those that don't support the *nix way of doing it (e.g. ntfs)

You can set the umask at any time.  The last umask setting is what is used.  If you set the umask from the CLI (e.g. umask 0077) and the touch a new file (e.g touch umask.test) you will get the permissions of rw------- until you close the session or restate the umask.

---

