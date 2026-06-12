---
title: "Move file from &quot;Read Only&quot; disc."
date: 2012-10-07
forum: Server Platforms
---

### Post by xb2003 on 2012-10-07
Hey, 
I mounted a CD i burned with a file that im trying to get onto my server, running 10.04 Server. But i get an error saying "Cannot Remove 'file' :Read-Only file system. Anything i can do about that?

Thanks.

---

### Post by Crafty Kisses on 2012-10-08
If you don't have root and can't get root, you can't run ```
mount -o remount,rw /media/disk
```Any mount command even the default user account requires SYS_ADMIN. What are the results of 
```
dmesg
```

---

### Post by Lars Noodén on 2012-10-08
> **xb2003 said:**
> Hey, 
I mounted a CD i burned with a file that im trying to get onto my server, running 10.04 Server. But i get an error saying "Cannot Remove 'file' :Read-Only file system. Anything i can do about that?

Thanks.

Try copying the file rather than moving it.  How are you trying to work with that, via the shell or via a graphical file manager?

---

### Post by Wim Sturkenboom on 2012-10-08
With the exception of UDF, CD is read-only. Nothing that one can do about that.

If it's a RW, you can wipe it. And else give it some decent scratches if your requirement is that nobody can access it.

---

### Post by xb2003 on 2012-10-08
Ok, thank you for the responses. Copying the file worked. I cant believe i didnt think of that from the start...

Thanks for the help.

---

