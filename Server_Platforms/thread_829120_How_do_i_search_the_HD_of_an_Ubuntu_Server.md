---
title: "How do i search the HD of an Ubuntu Server?"
date: 2008-06-14
forum: Server Platforms
---

### Post by r2000 on 2008-06-14
Hi, im kinda new to Ubuntu Server and was wondering what the command line syntax is for searching the HD for a specific file?

i.e I want to search for all instances of php.ini or all .conf files in all partitions of the HD.

Many thanks for any help, i did search the forums but it came back with wrong results, so i have posted here.

---

### Post by ajgreeny on 2008-06-14
```
locate .conf
``` will do it but also get anything with letters etc following the .conf.  To avoid that use```
locate -b .conf
```

---

### Post by r2000 on 2008-06-14
Thanks for your help, much appreciated.

One last question, if it can be answered here, which is most probable.

Do you know if ISPConfig on Ubuntu Server uses a default php.ini for all of the domains it controls?  I need to make a change to fsock, so that it is on.

Thanks.

"As a Windows Server user, I can say it was much easier and quicker setting up a fully functional Ubuntu web server than setting up Windows Server 2008 with Helm support. And the good thing is, is that Ubuntu is totally FREE"

---

### Post by r2000 on 2008-06-14
I have just tried the locate command under "su" and it returns the error:

"mlocate: cannot open `/var/lib/mlocate/mlocate.db' : no such file or directory"

Do I need to download an extra package?

---

### Post by hyper_ch on 2008-06-14
you first need to create/update the db:

```

sudo updatedb

```

or you can use the

```

find

```

command

---

