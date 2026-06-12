---
title: "Problem mounting internal drive from fstab"
date: 2012-10-14
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by philhughes on 2012-10-14
I just upgraded to 12.10 from 12.04 and have trouble mounting an internal drive from fstab.

I have an ssd (system/home) and two internal hard drives, one for data and one for storing backups. There are two entries in fstab as follows:

UUID=2cb4aef5-637c-44fa-b7a2-d4ba52f98545 /media/data           ext4    defaults        0       2
UUID=de6514b0-b7a9-49ca-a7ab-c19be1431636 /media/Backup\040Drive	ext4	defaults	0	2

When I boot up, I just get a black screen. Pressing Ctrl-Alt-F6 gets me the X console which shows:

An error occured while mounting /media/Backup Drive.
Press S to skip mounting or M for manual recovery.

If I press S, booting continues ok.

data is mounted as expected with owner root, Backup Drive is mounted with owner phil.

(Unmounted, both /media/data and /media/Backup Drive have owner root and permissions 755).

The following is shown in /var/log/boot.log:

mountall: Event failed
mount: /dev/sdc1 already mounted or /media/Backup Drive busy
mount: according to mtab, /dev/sdc1 is already mounted on /media/Backup Drive
mountall: mount /media/Backup Drive [824] terminated with status 32
mountall: Filesystem could not be mounted: /media/Backup Drive

(If I comment out the line for Backup, boot procedds ok, it doesn't get mounted and there are no entries in boot.log).

This all worked fine in 12.04. 2 questions:

1. Why is this happening now and any suggestions to fix it? (possibly something to do with udisks2?)
2. Why do I need to press Ctrl-Alt-F6 to see the console?

Thanks

---

### Post by ranger1021994 on 2012-10-14
Run fsck to check your disks.Maybe they are corrupt
Ctrl+Alt+F6 starts command line version.Its useful when there are problems related to desktop environment

---

### Post by philhughes on 2012-10-14
fsck reports partition as clean. Meant Ctrl-Alt-F7:).

---

### Post by ranger1021994 on 2012-10-14
> **philhughes said:**
> fsck reports partition as clean. Meant Ctrl-Alt-F7:).

Force an fsck at next reboot

[http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/](http://www.cyberciti.biz/faq/linux-force-fsck-on-the-next-reboot-or-boot-sequence/)

and then tell the output

---

### Post by dino99 on 2012-10-14
check the disks settings into : system tools -> prefs -> disk  Applications menu

---

### Post by philhughes on 2012-10-14
Forced fsck ob reboot. No problems, but exactly the same thing happens. boot.log has the same entries. I don't think this has anything to do with a bad disk.

---

### Post by steeldriver on 2012-10-14
Can we see the whole /etc/fstab please? plus the output of 'mount'

Maybe in 12.10 gnome-volume-manager is more picky about reserving /media for removable devices?

---

### Post by DuckHook on 2012-10-14
Also, try changing:

```
/media/Backup\040Drive	ext4	defaults	0	2
```

to

```
/media/Backup_Drive	ext4	defaults	0	2
```

to see what happens. Escaping the space character could create problems if the new mounting procedure internally processes the line twice.

---

### Post by philhughes on 2012-10-14
DuckHook - you seem to have hit on the problem. Mounting to /media/Backup_Drive and changing the line in fstab to what you suggested fixes the problem (ie it mounts ok).

Can you explain though what you mean about it porcessing the line twice?

---

### Post by DuckHook on 2012-10-15
> **philhughes said:**
> Can you explain though what you mean about it porcessing the line twice?

The problem was the space character in the HD name.

Linux treats spaces as the delimiter for either arguments or switches to follow. Therefore, it parses your HD name as: Mount a HD named "Backup" and apply a process to it called "Drive". Since there is no such process as "Drive", your mount process gives up and generates an error. You attempted to fool your system with the \040 escape sequence. But this works if only one process is involved. However, if it is necessary for the first process to pass the name string on to a second process, the first process will have already converted the \040 sequence to a space character and the second process will choke for the reason outlined above.

In short, don't ever use spaces in anything having to do with Linux. If you want readability, get into the habit of substituting the underscore character "_" for a space character. It will save you loads of trouble in future.

---

### Post by funicorn on 2012-10-15
No. op said "it works with no problem in 12.04"

> **DuckHook said:**
> The problem was the space character in the HD name.

Linux treats spaces as the delimiter for either arguments or switches to follow. Therefore, it parses your HD name as: Mount a HD named "Backup" and apply a process to it called "Drive". Since there is no such process as "Drive", your mount process gives up and generates an error. You attempted to fool your system with the \040 escape sequence. But this works if only one process is involved. However, if it is necessary for the first process to pass the name string on to a second process, the first process will have already converted the \040 sequence to a space character and the second process will choke for the reason outlined above.

In short, don't ever use spaces in anything having to do with Linux. If you want readability, get into the habit of substituting the underscore character "_" for a space character. It will save you loads of trouble in future.

---

### Post by philhughes on 2012-10-15
Thanks for the explanation DuckHook. However, IMO it is a long time since Linux didn't like spaces. This looks like a bug to me:

- it used to work in 12.04
- the use of \040 in fstab is widely recommended (though I can't find what I consider an authorative source)
- I have external USB drives that are automatically mounted by the system in /media/<user>/ using the drive label with a space in the name and this continues to work fine in 12.10

I will see if I can find any bug reports.

Also, ther seems to be another bug in that it stops the x console being displayed (I've realised that I actually have to press Ctrl-Alt-F1 before Ctrl-Alt-F7 to get the display).

---

### Post by funicorn on 2012-10-15
try this
UUID=de6514b0-b7a9-49ca-a7ab-c19be1431636 /media/Backup\040Drive	ext4 errors=remount	0	2

I think the reason might be the upstart script /etc/init/mountall-shell.conf runs with errors.

---

### Post by philhughes on 2012-10-15
funicorn - errors=remount makes no difference.

---

