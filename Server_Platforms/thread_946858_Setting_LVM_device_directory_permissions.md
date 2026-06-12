---
title: "Setting LVM device directory permissions"
date: 2008-10-13
forum: Server Platforms
---

### Post by vertigo23 on 2008-10-13
I use LVM2 on my servers, and volume group directories in /dev/ are created thusly:

$ ls -ld /dev/vg01
drwx------ 2 root root 200 2008-10-13 13:12 /dev/vg01/

I would like to have these directories be readable by the 'disk' group, like so:

$ ls -ld /dev/vg01
drwxr-x--- 2 root disk 200 2008-10-13 13:12 /dev/vg01/

I know this is typically done in /etc/udev/rules.d/ somewhere, but I can't find the rules for LVM's permissions.  Anyone know?

Thanks,
Alex :confused:

---

### Post by promodus on 2008-10-13
I'm going to guess /etc/lvm/lvm.conf

```
 # The file creation mask for any files and directories created.
    # Interpreted as octal if the first digit is zero.
    umask = 077
```

---

### Post by vertigo23 on 2008-10-14
> **promodus said:**
> I'm going to guess /etc/lvm/lvm.conf


Well, that works for the permission bits, but not for setting the GID.  I want to allow read-access to members of the 'disk' group (ie. sysadmins).  Your suggestion is a step in the right direction though - thanks.

---

