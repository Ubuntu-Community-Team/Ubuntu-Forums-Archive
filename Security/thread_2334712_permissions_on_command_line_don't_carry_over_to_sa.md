---
title: "permissions on command line don't carry over to samba"
date: 2016-08-21
forum: Security
---

### Post by kenz71 on 2016-08-21
Maybe I am making this more complicated than it needs to be - I suppose that can be said often for security.

Anyway - I have a series of directories that I can browse from the command line using Putty but using the same user ids from a Win10 box I can't access the same shares via Samba.  What am I doing wrong?

Here is the directory on the Ubuntu Server:
```

drwxrwxr-x 201 jenny g-dlna   204 Jul 16 10:14 Music
drwxrwx---   9 jenny g-adults  34 Jul 19 15:05 OurDocs
drwxrwx---   2 ken   g-adults   3 Aug 21 22:23 Test

```

When trying to browse the shares from Windows 10 useing either user name jenny or ken I get an error indicating "you don' t have permission to access \\UBUNTUSRV\Test"

If I chmod 777 the directory then the shares work - what the freak??? Is group permissions not working in Samba?

What I am running:
Samba version 4.3.9-Ubuntu for the server

Windows 10 on the client

It's got to be error 12 (12 inches from my screen i.e. user error!!)

---

### Post by ajgreeny on 2016-08-22
Thread closed.
Duplicate at [https://ubuntuforums.org/showthread.php?t=2334713&p=13534319#post13534319](https://ubuntuforums.org/showthread.php?t=2334713&p=13534319#post13534319)

Please do not create duplicate threads; it dilutes forum resources and can be very confusing for all.

---

