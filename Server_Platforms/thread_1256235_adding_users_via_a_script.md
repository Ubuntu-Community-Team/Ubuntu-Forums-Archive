---
title: "adding users via a script"
date: 2009-09-02
forum: Server Platforms
---

### Post by kchakrak on 2009-09-02
Is it possible to design a matrix (such as a csv) that the users can fill in with all their appropriate details and then can be directly imported? just to make adding endless numbers of users easy.

If this is not possible then is there any way of making adding large numbers of users a quicker task?

Using Ubuntu 8.04 server.

---

### Post by cdenley on 2009-09-02
It is possible.
```

useradd -p `mkpasswd -m SHA-512 $NEWPASS` $NEWUSER

```
If you're using 8.04 or earlier, you must replace SHA-512 with md5.

---

### Post by koenn on 2009-09-02
```
newusers
```
takes an input file in /etc/passwd format : 1 record per line, fields separated by ';'


```
man newusers
```
example here: [http://adminlinux.blogspot.com/2009/03/creating-bulk-users-in-linux.html](http://adminlinux.blogspot.com/2009/03/creating-bulk-users-in-linux.html)

---

### Post by kchakrak on 2009-09-03
Thanks for the help guys, I've got a few ideas now so I'll get to trying out what suits me best, or what works best.

Thanks Again,

---

