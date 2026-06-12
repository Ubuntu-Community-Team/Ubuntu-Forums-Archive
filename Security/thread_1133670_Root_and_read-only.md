---
title: "Root and read-only"
date: 2009-04-23
forum: Security
---

### Post by subi211 on 2009-04-23
Currently, we have to run as root, as we use NetBeans to compile and run an application which has to access port 1000 (This is a limitation applied to us by the hardware we're connecting to, so there's nothing we can do about it).

NetBeans does not offer any means of running applications through sudo, so the only way to give apps being debugged access to ports below 1024 is to run entirely as root.

Can anybody offer any suggestions as to a better solution?  I really don't like having everyone in the office running as root.

Being root has another problem, that being that root users can, by default, edit and write over read-only files with no warning.  This breaks our source database, as NetBeans thinks all files are RW.

Is there any way to prevent root users from writing to RO files?

Thanks!

---

### Post by some_random_noob on 2009-04-23
I'm no expert, but maybe you could try editing the sudoers file and only allowing certain commands to be run as sudo?

---

### Post by cdenley on 2009-04-23
> **some_random_noob said:**
> I'm no expert, but maybe you could try editing the sudoers file and only allowing certain commands to be run as sudo?

Create a group "netbeans", then add all users that need to start a server on port 1000 to that group. Then, edit your sudoers file
```

sudo EDITOR=nano visudo

```
by adding this line at the end
```

%netbeans ALL = (ALL) /path/to/myserver

```
Then, your users don't need any root access except to run your specific application.
```

sudo /path/to/myserver

```

---

