---
title: "NTFS Data recovery from Ubuntu Live CD"
date: 2010-12-06
forum: Security
---

### Post by trwats on 2010-12-06
I have a windows install that is totally hosed, bluescreens, etc. I want to try to force mount it from Ubuntu to get whatever data I can, but it won't allow me to mount. It keeps telling me to run chkdsk /f and reboot twice. But that's not possible. I was wondering if there are any ntfs tools for Ubuntu or any data recovery tools I can use to get what I can from this drive.

---

### Post by FuturePilot on 2010-12-06
If you have the Windows CD you could probably boot that and get into the recovery console and run chkdsk from there. If not you can use the "force" option to mount it from Ubuntu. Note that this has a warning, but considering it sounds hosed anyway, it's worth a try.

> force  Force the mounting even if the NTFS logfile is unclean. The logfile will be unconditionally cleared. Use this option with  caution and for your own responsibility.

```
sudo mount -t ntfs-3g volume mount_point -o force
```

---

### Post by WinstonChurchill on 2010-12-07
> **FuturePilot said:**
> ```
sudo mount -t ntfs-3g volume mount_point -o force
```

Add '**-r**' to the above make the mount read-only

That way, you can at least ensure it doesn't get worse... although it may still attempt to replay the journal as with ext3/ext4 - not sure what the normal behaviour is there.

**EDIT: **Maybe take a look at this: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery). It's aimed at deleted files, but some of the tools might prove useful.

---

### Post by TheFr00n on 2010-12-08
I don't think Ubuntu is going to be your weapon of choice for this, much as I love the OS. Google for apps like Recuva or GetDataBack for NTFS - either one will help.

I am not 100% certain of the legality, but it might also be worth googling for Hiren's BootCD - it's a bootable CD of tools for just such a situation as this.

---

