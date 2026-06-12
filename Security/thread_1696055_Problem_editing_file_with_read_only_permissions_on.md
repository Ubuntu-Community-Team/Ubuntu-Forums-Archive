---
title: "Problem editing file with read only permissions on a debian install"
date: 2011-02-26
forum: Security
---

### Post by Tiredofregisteringtoreg on 2011-02-26
Hey all!

I'm having an issue getting write permissions on a file stored on the root of my flash drive. I was trying to access the file via Ubuntu 10.10 that was installed on another flash drive.  The Debian install is on another drive for my Playstation 3, which is the drive i'm trying to access. On Ubuntu, I gave my self root access and tried two chmod commands being chmod ug+rw /media/ and chmod 754 /media. When I do that, I lose access to the drive. If i choose the location of the file, it says I can't access the file or the location doesn't exist. Any clue how would I solve this issue?  :?

---

### Post by CharlesA on 2011-02-26
What format is the flash drive? If it's FAT, you can't chown or chmod files on it.

What error is it giving you when you try to access the folder or files?

---

### Post by Tiredofregisteringtoreg on 2011-02-26
It's formated as ex4. I'll post the exact message when I get a chance to log back into ubuntu in a few mins.

---

### Post by Tiredofregisteringtoreg on 2011-02-26
This is what I just got when I tried to use the chmod command.

root@ubuntu:/media# chmod ug+rw /media/Ps3 Linux/kboot.conf
chmod: cannot access `/media/Ps3': No such file or directory
chmod: cannot access `Linux/kboot.conf': No such file or directory

The directory is there, I mean I couldn't read the kboot.conf file if it wasn't! THe permissions for the file are set as:

Onwer: root
Group: root

It also says SELinux context: unknown

I can read the files, but I can't write to them.

---

### Post by CharlesA on 2011-02-26
You need to escape spaces (or just use tab completion).

Post the output of this:

```
ls -ld /media/Ps3\ Linux
```

---

### Post by Tiredofregisteringtoreg on 2011-02-26
I get this

drwxr-xr-x 23 root root 4096 2011-02-26 05:59 /media/Ps3 Linux

Never mind I got it now, thanks!

---

