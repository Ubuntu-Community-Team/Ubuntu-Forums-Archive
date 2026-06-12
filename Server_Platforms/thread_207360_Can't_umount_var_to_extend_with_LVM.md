---
title: "Can't umount /var to extend with LVM"
date: 2006-07-01
forum: Server Platforms
---

### Post by saaz on 2006-07-01
/var is a logical volume on my system and is at 100% capacity now. Traditionally, in UNIX and all other Linux distros I've been able to boot into 'single' and do an lvextend on the lv in question. I've tried this with Ubuntu and see that 'single' doesn't appear to mean what it does in other distro's. Ubuntu loads all kinds of unneccessary garbage in single mode like X and GDM. It also insists on mounting EVERY filesystem listed in /etc/fstab. I've never seen this odd behaviour in another UNIX or Linux (and I've been at this professionally for over 10 years now). 

Complaints aside, any ideas how I can umount /var?? I can do an 'fuser -v' on /var (or the device) and it produces no output (alas, another command which, unfortunately, appears to have been watered down compared to it's UNIX counterpart.) Of course, if I try to umount /var it says "filesystem is busy."

---

### Post by eldaria on 2006-10-31
I have the same issue but with my /home I run lvextend and it completes fine.
but a resize2fs produces followinf output:
```

># resize2fs /dev/raidvg/homelv
resize2fs 1.39 (29-May-2006)
Filesystem at /dev/raidvg/homelv is mounted on /home; on-line resizing required
Performing an on-line resize of /dev/raidvg/homelv to 26214400 (4k) blocks.
resize2fs: Operation not permitted While trying to add group #640

```


How can I extend the lvm?
If it is not possible then lvm is kind of without purpose?

---

### Post by EmmEff on 2006-12-12
Any resolution to this?  I am trying to resize the root partition while it's mounted.

---

### Post by eldaria on 2006-12-12
Well I was unable to resolve it so, changed from Ext3 to ReiserFS, since this one can be resized while mounted and in use.
Well at least I have been able to Extend it, did not try to reduce.

---

### Post by EmmEff on 2006-12-12
I am not interested in converting the filesystem.  Thanks anyway.

---

### Post by gnaunited on 2006-12-12
Nothing like that should be loading - single should be a command line. Check to make sure you are booting into the correct mode.

---

### Post by chalex on 2006-12-12
You don't have to reboot, right? You can just type "telinit 1" or "runlevel 1" as root.

---

### Post by gnaunited on 2006-12-12
Even when you do that it should kill gdm and take everything with it. Even so it is always better to reboot into it cause it is a true single user mode.

---

