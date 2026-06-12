---
title: "Locked File System"
date: 2007-02-04
forum: Ubuntu System Panel
---

### Post by danbar on 2007-02-04
As I click on File system to see the files that I have on the hard disk, I see that there is the sign of a lock.  Consequently I cannot see the files.  Is there any way of UNLOCKING the file system?  

As I played about with the cursor, it told me that I'm not the owner and cannot change the permissions!! Any solution?

Thanks for your time and patience. :KS

---

### Post by FluorescentDuck on 2007-02-04
Hello there,

I had this same problem when I first installed Ubuntu. From the terminal:

```
sudo chown -R yourusername:yourusername "file or folder path here"
```

Make sure you only change file permission for files that actually belong to you - if you want to edit system files, use sudo.

---

### Post by danbar on 2007-02-04
:~$ sudo chown -R (my username) "file or folder path here"
Password:
chown: cannot access `file or folder path here': No such file or directory
(my username)desktop:~$ sudo chown -R
chown: missing operand
Try `chown --help' for more information.
(my usename)-desktop:~$ sudo chown - R my username
chown: `-': invalid user


This is the result.  I'm copying from the terminal window.

---

### Post by FluorescentDuck on 2007-02-04
> **danbar said:**
> :~$ sudo chown -R (my username) "file or folder path here"
Password:
chown: cannot access `file or folder path here': No such file or directory
(my username)desktop:~$ sudo chown -R
chown: missing operand
Try `chown --help' for more information.
(my usename)-desktop:~$ sudo chown - R my username
chown: `-': invalid user


This is the result.  I'm copying from the terminal window.

:neutral: Hm..maybe I can explain this better with an example. 

If your username was danbar, and you wanted to change the file permissions for a folder with the path "/home/Stuff", you would type:

```
sudo chown -R danbar:danbar "/home/Stuff"
```

If you're unsure what to type as the folder path, simply find that folder in your filesystem and copy the path into the terminal.

---

### Post by danbar on 2007-02-04
Nothing is happening now!  Under file system there are two folders: Home and Media.  Now under media there are only CDrom and Floppy!

What I need to see is the hard disk where Ubuntu is installed hdb1.  

I have dual boot.  Where on the other hard disk there is win xp.  Obviously that would be the second step, to see the other hard disk.  But I was told that the lock (visible) near the File System is blocking any viewing efforts!

Many thanks for your time!

---

### Post by FluorescentDuck on 2007-02-04
Hm...I thought this was a problem with file permissions within the hard drive. I have no idea how to unlock a hard drive itself - you could try using sudo chown on the hard drive but I doubt it'll work. Sorry.:(

---

### Post by chanders on 2007-02-04
Guys, I think you all are in the wrong forum ;-)

Mods, mind moving to the appropriate forum?

---

### Post by Big_Croc7 on 2007-02-05
I'm not sure exactly what you're trying to do, but I'll try to help.  If you see a little picture of a lock symbol, that usually means the folder/directory is read-only, so you should be able to see its contents but not write to it (a cross shows that you can't read it either).

If you go to the Places menu then click Computer you should see the mounted partitions on your drive (with their volume names).

If you are having problems with permissions, you can access any files through nautilus by typing the command 'gksudo nautilus' in the terminal - but be warned, this runs a session of nautilus with root access, which makes it very easy to mess up your system accidentally!

If you want to mount a partition (e.g. your Windows volume) try going to system, administrator, disk management - this should allow you to mount volumes so you can read the files.

---

