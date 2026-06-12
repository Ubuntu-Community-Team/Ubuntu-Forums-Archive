---
title: "Why are DEs able to do some things without root privileges?"
date: 2007-08-18
forum: The Cafe
---

### Post by nrwilk on 2007-08-18
I have been wondering about this for a while, but haven't ever gotten around to asking about it.

It seems that the DEs are able to do some things without root privileges that a normal user cannot do with non-root privileges.

The most obvious things that I can think of are shutting the system down, rebooting, mounting drives, unmounting drives, and making bluetooth connections.

I just realized as I was typing this that KDM and GDM get instantiated before any user actually logs in.  Does this have something to do with it?  I was thinking about this with the impression that KDE and Gnome run under the user's UID, but I guess that could be wrong.  Are they run with superuser privileges?  What about other processes like knetworkmanager and KbluetoothD which are obviously run with the user's UID?  How do these programs make connections without root permissions?  How does qtparted mount and unmount drives while running under a UID other than 0?

Thanks for any help enlightening me on this! :)

---

### Post by Kimm on 2007-08-18
I would think that it somehow communicates with the DM (GDM, KDM, etc.) as it actually runs as root.

> **nrwilk said:**
> How does qtparted mount and unmount drives while running under a UID other than 0?

I have never used qtparted, but I know that at least gparted refuses to start without root privileges.

---

### Post by Miguel on 2007-08-18
gdm is indeed run as root:
```

$ ps aux | grep gdm
root      4865  0.0  0.2  13576  1356 ?        Ss   Aug18   0:00 /usr/sbin/gdm
root     15052  0.0  0.5  14024  2716 ?        S    Aug18   0:00 /usr/sbin/gdm
root     15292  3.6 13.0  79388 67396 tty9     Ss+  Aug18  15:15 /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt9
miguel   20771  0.0  0.1   2996   776 pts/0    R+   00:49   0:00 grep gdm

```

---

### Post by Bachstelze on 2007-08-18
> **Miguel said:**
> gdm is indeed run as root:
```

$ ps aux | grep gdm
root      4865  0.0  0.2  13576  1356 ?        Ss   Aug18   0:00 /usr/sbin/gdm
root     15052  0.0  0.5  14024  2716 ?        S    Aug18   0:00 /usr/sbin/gdm
root     15292  3.6 13.0  79388 67396 tty9     Ss+  Aug18  15:15 /usr/bin/X :0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt9
miguel   20771  0.0  0.1   2996   776 pts/0    R+   00:49   0:00 grep gdm

```

Yep, and if you run the DE directly, as yourself (with e.g. *startx*), it won't let you shut down.

---

### Post by saulgoode on 2007-08-18
There is a file permission called "SUID" (Set User IDentity) which tells the kernel to execute the file as though the file's owner invoked the command. If you do an 'ls -l' on a file that has the SUID permission set, you will see an "s" instead of an "x" in the file permissions. 

For example:

[INDENT][I]ls -l /usr/bin/passwd
-rws--x--x 1 root root 34492 2006-08-22 16:08 /usr/bin/passwd*[/I][/INDENT]

When you execute 'passwd', the kernel will perform the command as though 'root' invoked it (because the owner of the file is 'root').

---

### Post by az on 2007-08-18
On a multiuser system, not everything runs as the user who is sitting in front of the monitor.

I believe that GDM and other desktop managers run libPAM which is Pluggable Authentication Modules library.  This is the mechanism by which the application (GDM) can log users in and juggle different levels of privileges.

---

### Post by Miguel on 2007-08-18
> **saulgoode said:**
> There is a file permission called "SUID" (Set User IDentity) which tells the kernel to execute the file as though the file's owner invoked the command. If you do an 'ls -l' on a file that has the SUID permission set, you will see an "s" instead of an "x" in the file permissions. 

For example:

[INDENT][I]ls -l /usr/bin/passwd
-rws--x--x 1 root root 34492 2006-08-22 16:08 /usr/bin/passwd*[/I][/INDENT]

When you execute 'passwd', the kernel will perform the command as though 'root' invoked it (because the owner of the file is 'root').

Cool! Thank you for your explanation. I've noticed those files with SUID are highlighted in a brown-garnet box in gnome-terminal, in case some of you wonder. In any case, were I to execute one of those binaries, shouldn't the process owner appear as "root" in top-like programs?

---

### Post by nrwilk on 2007-08-19
Thanks everyone!

That clears a lot up, it makes sense that KDM/GDM get instantiated as root.

So, KDM/GDM are more than just graphical login managers?  Do they also act as a layer to provide Gnome and KDE these types of functions which wouldn't usually be available without root permissions?

---

### Post by juxtaposed on 2007-08-19
> Yep, and if you run the DE directly, as yourself (with e.g. startx), it won't let you shut down.

Or you type sudo reboot :)

But i've never been able to shutdown from the commandline.

---

### Post by nrwilk on 2007-08-19
> **juxtaposed said:**
> Or you type sudo reboot :)

But i've never been able to shutdown from the commandline.

you can use either of these:
```
halt
```
```
shutdown -P now
```

---

