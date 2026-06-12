---
title: "File server with users of Active directory"
date: 2011-05-26
forum: Security
---

### Post by vivamotos on 2011-05-26
Hello,

I want to create a shared folder in a ubuntu sistem but I want to know if I can get access to some users of my domain active directory windows 2003 server?

If I can, I would give that security in some of the subfolders of that shared folder as explained at the example:

EXAMPLE:

Backups (all have access and it's shared)
    Mail of Charles (Can only have access Charles that have an account on domain)
    Mail of John  (Can only have access John)
...

Do you know how to do it?

---

### Post by Lars Noodén on 2011-05-26
You can integrate [samba with active directory](http://wiki.samba.org/index.php/Samba_%26_Active_Directory).  Samba will give you the file sharing you want with linux, mac and windows users even though AD is a terrible, terrible mess.  There is a lot of information how to do this at the main Samba site and here in the [forum](http://ubuntuforums.org/showthread.php?t=91510).

---

