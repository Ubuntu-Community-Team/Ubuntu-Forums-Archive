---
title: "Whats up with SUDO?"
date: 2008-05-15
forum: Security
---

### Post by prenger745 on 2008-05-15
Until just now I have been able to open a terminal window and type 'sudo' then whatever I wanted to do. It would ask for my password, I would enter it and it would run my command.  Now, all of a sudden, when I type sudo (+some command) I get this:

dmcgurk@dan:~$ sudo fdisk -1
sudo: must be setuid root
dmcgurk@dan:~$ 

Not only that, now when I try to mount my harddrive I get this error:

Error org.freedesktop.DBus.Error.AccessDenied

Details:

A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "org.freedesktop.Hal.Device.Volume" memeber "Mount" error name "(unset)" destination "org.freedesktop.Hal")


I have no idea what I did or how to fix it :-(

Thanks,
Dan

---

### Post by unutbu on 2008-05-15
I'm not sure I know how to solve your problem, but it might be helpful to boot from the LiveCD so you can use a different operating system to examine your hard drive.

Then mount your hard drive at, (just for specificity) say, /media/disk.

In a terminal:
```

% ls -l /media/disk/usr/bin/sudo
```

It should look like this:
```

-rwsr-xr-x 1 root root 91776 2007-06-15 08:49 /usr/bin/sudo
```

Notice the 's' in the permissions line. That indicates sudo has the suid bit set. The error message 

```
sudo: must be setuid root
```

seems to suggest this bit is not set.
If you find that your suid bit is not set, then the fix may be to reinstall the sudo package. You may need some special instructions to do this without the sudo command. Post if you're having trouble with that.

Also, this will not explain how your machine ended up like this, and it may be worth trying to figure that out so this doesn't happen again.

The

```
Error org.freedesktop.DBus.Error.AccessDenied
```

seems to be generated when some config file in 
/etc/dbus-1/system.d is not right. See

[http://osdir.com/ml/debian.devel.evolution/2006-09/msg00024.html](http://osdir.com/ml/debian.devel.evolution/2006-09/msg00024.html)

Unfortunately, blindly following that poster's solution probably won't work since his problem was somewhat different. I don't know exactly what you'd need to fix yours, short of reinstalling the dbus package.

---

### Post by BlueSkyNIS on 2008-05-15
Follow unutbu suggestions and setuid can be set with:

(following his example)
```
chmod u+xs /media/disk/usr/bin/sudo
```

---

### Post by Dr Small on 2008-05-15
> **BlueSkyNIS said:**
> Follow unutbu suggestions and setuid can be set with:

(following his example)
```
chmod u+xs /media/disk/usr/bin/sudo
```
Why not boot into recovery mode and run that command?? ;)

---

### Post by BlueSkyNIS on 2008-05-15
> **Dr Small said:**
> Why not boot into recovery mode and run that command?? ;)

In that case the command would be:

```
chmod u+xs /usr/bin/sudo
```


Cheers ;)

---

### Post by unutbu on 2008-05-15
In recovery mode you have to preface the chmod command with 'sudo'. His sudo is not working, so I sent him to the LiveCD.

---

### Post by amingv on 2008-05-15
> **unutbu said:**
> In recovery mode you have to preface the chmod command with 'sudo'. His sudo is not working, so I sent him to the LiveCD.

No, in recovery mode you get a root shell. You don't need to grant root privileges to root :).

---

### Post by unutbu on 2008-05-15
Ah! You are right. Thanks.

---

### Post by conscious on 2008-05-15
> **prenger745 said:**
> dmcgurk@dan:~$ sudo fdisk -1

You probably want to run ```
sudo fdisk -l
``` with lowercase "L", not "one".

---

### Post by Oldsoldier2003 on 2008-05-15
> **conscious said:**
> You probably want to run ```
sudo fdisk -l
``` with lowercase "L", not "one".

even so fdisk would have returned ```
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

```
so that isn't the problem

---

### Post by Arthur Archnix on 2008-05-15
Something like that might occur if you mounted your disks with the nosuid option in fstab. Maybe?

---

