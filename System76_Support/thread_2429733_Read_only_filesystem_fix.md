---
title: "Read only filesystem fix?"
date: 2019-10-22
forum: System76 Support
---

### Post by michaelmcole on 2019-10-22
Hey all,
Ubuntu 19.10 on a System76 Kudu laptop

So I have a second HD in my laptop that i've never used, and I've discovered that it wasn't even mounted...
So, I made this entry in my /etc/fstab

```
UUID=e811bcf7-fbf1-4822-91ba-73cc0d52b6c7 /media/terra    ext4    user,errors=remount-ro,auto,exec,rw 



```

And that seemed to work, I can see the drive now, but I can't change anything - "Read-only filesystem"

Does anyone know how I can fix this?

I can provide more info if you tell me what you need.

---

### Post by slickymaster on 2019-10-22
*Thread moved to **System76 Support**.*

---

### Post by uRock on 2019-10-22
Does it allow you to [chown]("https://www.computerhope.com/unix/uchown.htm") it?

---

### Post by TheFu on 2019-10-22
Not a System76-specific question.

Anyways, a read-only file system is the way that the OS tries to protect storage from more corruption.  

a) The fstab entry is missing 2 columns on the far right.  These are critical.
b) You should umount the  /media/terra    and run an fsck against the file system device.  It is mapped from the UUID, but we can't see which device it should be or even if the UUID used is correct.  **lsblk** output would help greatly.
c) if the fsck doesn't fix the issue, then checking the HDD for SMART problems would be my next step.  smartctl is the tool, smartmontools is the package name (I think).  Run a test, then run a report using smartctl.

---

### Post by michaelmcole on 2019-10-22
oh my freaking god, how did i not realize that??!?

thank you uRock!

shuffles away mumbling....

---

### Post by michaelmcole on 2019-10-22
> **TheFu said:**
> Not a System76-specific question.



yea, not sure why slickymaster moved it.

---

### Post by TheFu on 2019-10-22
> **michaelmcole said:**
> yea, not sure why slickymaster moved it.

Because it contained an unnecessary keyword?
Providing just enough relevant information is a fine line.

Did the chmod work?  If so, please say that and mark the thread "*SOLVED*" using the thread-tools button so other people don't waste time.

---

### Post by uRock on 2019-10-22
> **michaelmcole said:**
> oh my freaking god, how did i not realize that??!?

thank you uRock!

shuffles away mumbling....

Permissions is why I decided to start adding drives to fstab and creating all of my logins with the same username.

---

