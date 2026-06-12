---
title: "user group question"
date: 2010-06-17
forum: Security
---

### Post by yilin on 2010-06-17
```
abcd@workbook:~$ groups abcd
abcd : abcd adm dialout fax cdrom floppy tape dip video plugdev users fuse admin www cvs
```

user abcd is in the group www

```
abcd@workbook:/home/www$ ls -l
total 4
drwxrwxr-x 17 root www 4096 2010-06-17 16:31 htdocs
abcd@workbook:/home/www$ 
```

htdocs is writable by group users (is my understanding correct?)

```
abcd@workbook:/home/www/htdocs$ ls > ll
bash: ll: Permission denied
```

but user abcd cannot write to htdocs.

This is on ubuntu 10.04, I don't know what's wrong, please help me to get the right working in htdocs.

Thanks

---

### Post by Bachstelze on 2010-06-18
Is there a file called ll in the dir already?

---

### Post by yilin on 2010-06-18
No. I was testing if I can write to htdocs

---

### Post by yilin on 2010-06-18
I logged into another account, edited www group again, although I didn't change anython, then came back. Things are worked!

---

### Post by FuturePilot on 2010-06-18
Yes you have to log out and back in a gain for group modifications to take effect.

---

### Post by bodhi.zazen on 2010-06-18
> **FuturePilot said:**
> Yes you have to log out and back in a gain for group modifications to take effect.

Or start a new login shell

```
su - bodhi
```

```
bash -l
```

---

