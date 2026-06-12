---
title: "Error mouniting Windows partition"
date: 2015-03-04
forum: Ubuntu Development Version
---

### Post by enricobe on 2015-03-04
Hello,
I have a problem with 15.04 after the upgrade from 14.10.
When I try to open the Windows partition from nautilus (click on the partition from the column on the left) it returns this error.
```

Error mounting /dev/sda4 at /media/enrico/TI31051200A: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda4" "/media/enrico/TI31051200A"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.
```
I have already tried to reboot and shut down Windows properly, but it still doesn't work. It has always worked fine with 14.10 and I got this error since I have upgraded to 15.04.
Has anyone the same error?

---

### Post by Cavsfan on 2015-03-04
I got that error and could not mount my C: partition. But, windows 7 was not properly shutdown and once I booted into it and let it load.
Then rebooted back to 15.04 I could then mount C:. So if that didn't fix it I don't have any idea what to do.

I only have gparted installed on Precise and unless I mount C: partition before I open gparted, it shows there is something wrong with C:.
If I mount it before hand it does not report any error with C:.

---

### Post by enricobe on 2015-03-04
I have already tried to shut down Windows properly, but i always got the same error. With 14.10 the auto-mount was working well, should I report it as a bug?

---

### Post by cariboo on 2015-03-04
> **enricobe said:**
> I have already tried to shut down Windows properly, but i always got the same error. With 14.10 the auto-mount was working well, should I report it as a bug?

You may want to try running chkdsk on your windows install

---

### Post by enricobe on 2015-03-05
> **cariboo907 said:**
> You may want to try running chkdsk on your windows install
I have done a scandisk, then rebooted on Windows and shut down again. Nothing changed. Always the same 
```

Error mounting /dev/sda4 at /media/enrico/TI31051200A: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda4" "/media/enrico/TI31051200A"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda4': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

```

EDIT:
I have installed the daily updates and after the reboot it works fine....

---

### Post by Rock 'n' Linux on 2015-05-29
enricobe, did you know what solved your issue? I seem to have the same problem. (See [http://ubuntuforums.org/showthread.php?t=2280282](http://ubuntuforums.org/showthread.php?t=2280282) )

---

### Post by cariboo on 2015-05-29
Seeing as Vivid has been released, there is no need for this discussion. Thread closed.

---

