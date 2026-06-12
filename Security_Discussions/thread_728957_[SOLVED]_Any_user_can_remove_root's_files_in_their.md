---
title: "[SOLVED] Any user can remove root's files in their home dir?"
date: 2008-03-19
forum: Security Discussions
---

### Post by unutbu on 2008-03-19
Is this behavior normal? I have never noticed this before.

```

11:24:46 cyrano@farmer:~% id
uid=1000(cyrano) gid=1000(cyrano) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),108(lpadmin),110(admin),115(netdev),117(powerdev),1000(cyrano)
11:24:47 cyrano@farmer:~% cd
11:24:49 cyrano@farmer:~% lsattr -d .
--------------I--- .
11:25:07 cyrano@farmer:~% ls -ld .
drwxr-xr-x 97 cyrano cyrano 16384 2008-03-19 11:24 .
11:25:10 cyrano@farmer:~% sudo touch rootownsthis
11:25:14 cyrano@farmer:~% ls -l rootownsthis 
-rw-r--r-- 1 root root 0 2008-03-19 11:25 rootownsthis

```

Note that users other than root only have read permission.

```

11:25:17 cyrano@farmer:~% rm rootownsthis 
rm: remove write-protected regular empty file `rootownsthis'? y
11:25:24 cyrano@farmer:~% ls -l rootownsthis 
ls: rootownsthis: No such file or directory

```

Normal user successfully removes root's file!

The reader can easily confirm that
1) a normal user can remove root's file in subdirectories of the home directory too.
2) the rootownsthis file can have a positive size and still be removable.


The same commands produce a different behavior in /tmp.

```

11:25:31 cyrano@farmer:~% cd /tmp
11:25:42 cyrano@farmer:/tmp% lsattr -d .
------------------ .
11:25:45 cyrano@farmer:/tmp% ls -ld .
drwxrwxrwt 10 root root 4096 2008-03-19 11:08 .
11:25:48 cyrano@farmer:/tmp% sudo touch rootownsthis
11:25:52 cyrano@farmer:/tmp% ls -l rootownsthis 
-rw-r--r-- 1 root root 0 2008-03-19 11:25 rootownsthis
11:25:54 cyrano@farmer:/tmp% rm rootownsthis 
rm: remove write-protected regular empty file `rootownsthis'? y
rm: cannot remove `rootownsthis': Operation not permitted
11:26:01 cyrano@farmer:/tmp% ls -l rootownsthis 
-rw-r--r-- 1 root root 0 2008-03-19 11:25 rootownsthis

```

---

### Post by honeydew on 2008-03-19
I can confirm this.. I would say that this is pretty strange behavior as well =/

---

### Post by ajgreeny on 2008-03-19
It looks as if you did the touch and rm commands within a very short time span and I think sudo remains active for several minutes, so if you do something like you did the password requirement will not be required.  Mind you I thought you still needed to preface the command with sudo in order to get it to even attempt to work, so I'm a bit baffled as well.  I know you can set the default sudo timeout to require that the password is needed for every command issued, but I can't remember how.  It's on this forum somewhere.

---

### Post by cdenley on 2008-03-19
Apparently, if you own the directory, you can delete any files in that directory. If you don't own the directory...
```

sudo mkdir test
sudo touch test/rootownsthis
rm test/rootownsthis
rm -rf test

```
you will get "permission denied". I tested on FreeBSD, works the same.

---

### Post by GhodMode on 2008-03-19
This is how it's supposed to work, but it's not really because it's in your home directory.  The ability to delete files in a directory are defined by the containing directory's permissions, not the file's permissions.  The files within a directory are considered the contents of the directory.  Therefore, if you have write permission on the directory, you have the ability to change its contents.  You don't, however, have the ability to change the contents of a file owned by root unless the file permissions allow you to do it.

ref: [http://www.albany.edu/faculty/gms/homepage101/unix_permissions.html#directory](http://www.albany.edu/faculty/gms/homepage101/unix_permissions.html#directory)

--
-- Ghodmode

---

