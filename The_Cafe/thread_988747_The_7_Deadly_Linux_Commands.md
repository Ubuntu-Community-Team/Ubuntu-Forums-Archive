---
title: "The 7 Deadly Linux Commands"
date: 2008-11-20
forum: The Cafe
---

### Post by sharks on 2008-11-20
The 7 Deadly Linux Commands 
[http://www.junauza.com/2008/11/7-deadly-linux-commands.html](http://www.junauza.com/2008/11/7-deadly-linux-commands.html)

---

### Post by damis648 on 2008-11-20
Ah, I thought the forkbomb was just called "fork". Good to know! :-)

EDIT: Wait... can you mv something to /dev/null? (Command 7) Will it even let you do that? You can't mv anything into a file...

---

### Post by saulgoode on 2008-11-20
> **damis648 said:**
> EDIT: Wait... can you mv something to /dev/null? (Command 7) Will it even let you do that? You can't mv anything into a file...
You can do it (assuming you have root privileges), but the results won't be immediately disastrous. Your /dev/null device will be replaced by a file, which will probably cause problems if you ever try to use /dev/null as a source of (what should be) zeros. In the more typical case of redirecting output to /dev/null, performance will harmed -- /dev/null should normally be something of a no-op -- and you could conceivably fill up your / device (i.e., the hard drive). Deleting the 'null' file and rebooting should correct things (or you could manually use 'mknod' to recreate the null device).

---

### Post by TBOL3 on 2008-11-20
You know, I applaud everyone for helping with this cause, but wouldn't it be better if people just didn't use a command, unless they new what it was doing?  (Except for shell scripts, for those, I gues you either have to read it all, or just trust the source).

---

### Post by iponeverything on 2008-11-20
> **saulgoode said:**
> You can do it (assuming you have root privileges), but the results won't be immediately disastrous. Your /dev/null device will be replaced by a file, which will probably cause problems if you ever try to use /dev/null as a source of (what should be) zeros. In the more typical case of redirecting output to /dev/null, performance will harmed -- /dev/null should normally be something of a no-op -- and you could conceivably fill up your / device (i.e., the hard drive). Deleting the 'null' file and rebooting should correct things (or you could manually use 'mknod' to recreate the null device).

```
mv something /dev/null  = rm something
```

/dev/null is not modified or changed in any way. And from low level file system perspective - I believe - they do the exact same thing. The former, for me, is like picking up a piece of data an putting it in the trash can and latter is like using a antimatter gun to disintegrate something.

BTW -- anyone can put stuff into /dev/null not just root.

---

### Post by saulgoode on 2008-11-20
> **iponeverything said:**
> ```
mv something /dev/null  = rm something
```

/dev/null is not modified or changed in any way. And from low level file system perspective - I believe - they do the exact same thing. The former, for me, is like picking up a piece of data an putting it in the trash can and latter is like using a antimatter gun to disintegrate something.

If the last argument of the 'mv' command exists and is not a directory, it is treated as a file and the attempt is made to replace it with the source file.
[INDENT]$ echo "replaced" >sourcefile
$ echo "original" >destfile
$ cat destfile
**original**
$ mv sourcefile destfile
$ cat destfile
**replaced**[/INDENT]

> **iponeverything said:**
> BTW -- anyone can put stuff into /dev/null not just root.
Nonetheless, only 'root' has permission to remove, rename, or create files in the /dev directory:
[INDENT]$ ls -ld /dev
**drwxr-xr-x 17 root root 14660 2008-11-20 22:02 /dev/**[/INDENT]

---

### Post by iponeverything on 2008-11-21
> **saulgoode said:**
> If the last argument of the 'mv' command exists and is not a directory, it is treated as a file and the attempt is made to replace it with the source file.
[INDENT]$ echo "replaced" >sourcefile
$ echo "original" >destfile
$ cat destfile
**original**
$ mv sourcefile destfile
$ cat destfile
**replaced**[/INDENT]


Nonetheless, only 'root' has permission to remove, rename, or create files in the /dev directory:
[INDENT]$ ls -ld /dev
**drwxr-xr-x 17 root root 14660 2008-11-20 22:02 /dev/**[/INDENT]

You are right. I don't know if it just my faulty memory or if things really changed somewhere along the line.  I should have just gave it quite test at the command line, before adding my 2 cents.

---

### Post by schauerlich on 2008-11-21
Is it just me or was most of that lifted from jdong's announcement?

[http://ubuntuforums.org/announcement.php?f=11](http://ubuntuforums.org/announcement.php?f=11)

---

### Post by kernelhaxor on 2008-11-21
> **EDavidBurg said:**
> Is it just me or was most of that lifted from jdong's announcement?

[http://ubuntuforums.org/announcement.php?f=11](http://ubuntuforums.org/announcement.php?f=11)


I don't think it is necessarily lifted from one place or the other .. they're jus common and known for their bad nature.. so you will find them in a lot of places (in the form of warnings I mean) ..

---

### Post by schauerlich on 2008-11-21
> **kernelhaxor said:**
> I don't think it is necessarily lifted from one place or the other .. they're jus common and known for their bad nature.. so you will find them in a lot of places (in the form of warnings I mean) ..

Not only are the commands the same, the descriptions are too. It's pretty obvious this guy just slightly reworded jdong's announcement.

[quote=7 Deadly Linux Commands]Known as forkbomb, **this command will tell your system to execute a huge number of processes until the system freezes**. This can often lead to corruption of data.[/quote]

[quote=jdong's announcement]Forkbomb: **Executes a huge number of processes until system freezes**, forcing you to do a hard reset which may cause corruption, data damage, or other awful fates.[/quote]

[quote=7 Deadly Linux Commands]With this command, **raw data will be written to a block device that can usually clobber the filesystem resulting in total loss of data.**[/quote]

[quote=jdong's announcement]Block device manipulation: **Causes raw data to be written to a block device. Often times this will clobber the filesystem and cause total loss of data**[/quote]

---

