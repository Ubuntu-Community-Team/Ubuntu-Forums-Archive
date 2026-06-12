---
title: "Help Me !!! Urgent !!! Apache Web Service can't Start"
date: 2018-02-02
forum: Server Platforms
---

### Post by cakrabirawa on 2018-02-02
Dear All Members,

Please help me, my web server down is now, the problem is like this:

 * Starting web server apache2                                                                                                                                                  mktemp: failed to create file via template ‘/tmp/tmp.XXXXXXXXXX’: No such file o                                                                                                r directory
/etc/init.d/apache2: 91: /etc/init.d/apache2: cannot create : Directory nonexist                                                                                                ent
 *
 * The apache2 configtest failed.


Please send me a solution, i don't know what next i do ???

Sorry about my english


Thank youo so much

---

### Post by wildmanne39 on 2018-02-02
Welcome to the forum!

*Thread moved to **Server Platforms, a more appropriate forum**.*

Please be patient we are all volunteers from all over the world so it may take time for the person that can help you to get online.

You can bump your thread once every twelve hours.

---

### Post by LHammonds on 2018-02-02
> **cakrabirawa said:**
>  ‘/tmp/tmp.XXXXXXXXXX’: No such file or directory
/etc/init.d/apache2: 91: /etc/init.d/apache2: cannot create : Directory nonexist                                                                                                ent
Sounds pretty obvious.

Does the "/tmp" folder exist?

Or is it full and cannot perform any operations on it such as creating a folder/file?

Have the permissions changed on "/tmp" where Apache can no longer access it?

Command to look at your disk space:
```
df -h
```

Command to look at your permissions on /tmp:

```
ls -l /tmp
```

LHammonds

---

