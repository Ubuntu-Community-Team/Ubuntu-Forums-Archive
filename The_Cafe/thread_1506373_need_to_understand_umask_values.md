---
title: "need to understand umask values"
date: 2010-06-10
forum: The Cafe
---

### Post by axel_2078 on 2010-06-10
I'm currently studying for the new Linux+ exam (Powered by LPIC) and I'm not completely understanding umask values. What I understand so far from my reading is that the umask is used to find the effective permissions for files and directories and it is calculated by subtracting it from the default values of directories (777) and files (666). Hence a umask of 022 would yield effective permissions of 755 for directories and 644 for files. That much I get. What I don't understand is how this Linux+ book I'm reading said a umask of 027 yields 750 for directories (the math works since 777-027=750) and yields 640 for files. The directory portion makes sense; the file portion doesn't. How do you subtract 6 from 7 (666-027) and get 0? This same Linux+ book also says that a umask of 013 will yield effective permissions of 764 for BOTH files and directories. How can that be?? They have different default permissions! By my math, that would yield effective permissions of 764 for directories and 653 for files, which is extremely weird. Can someone clear this up for me?

---

### Post by Bachstelze on 2010-06-10
If you want to think about it using math, you must think in binary. The effective permissions are calculated by doing a bitwise AND between the default permissions and the one-complement (bitwise NOT) of the umask value. For example, for a directory with a 022 umask:

```

umask:          000 010 010 (022)
one-complement: 111 101 101 
default:        111 111 111 (777)

result:         111 101 101 (755)

```

In the case of a umask of 027 for files:

```

umask:          000 010 111 (027)
one-complement: 111 101 000 
default:        110 110 110 (666)

result:         110 100 000 (640)
```

In plain English: the effective permissions will have all the bits that are active by default and *not* set in the umask. The umask is used to tell which permissions that are granted by default you wish to restrict, but it can not grant permissions that are not granted by default (hence why a file is never executable after creation, even with a umask of 000).

---

### Post by john_spiral on 2010-06-23
Found the below link very helpful when trying to get my head around the **umask** command

[http://www.sun.com/bigadmin/content/submitted/umask_permissions.jsp](http://www.sun.com/bigadmin/content/submitted/umask_permissions.jsp)

---

