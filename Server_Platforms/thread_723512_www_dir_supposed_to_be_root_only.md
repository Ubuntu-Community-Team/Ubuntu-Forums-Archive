---
title: "www dir supposed to be root only?"
date: 2008-03-13
forum: Server Platforms
---

### Post by android6011 on 2008-03-13
is apache2' www directory supposed to be root only? i cant put files files in the directory or edit them without using sudo

---

### Post by scragar on 2008-03-13
yes, you could chmod/chown it to make it user accessable, but that's a rather big security concern
```
chmod -R 777 /var/www
```

---

### Post by android6011 on 2008-03-13
i thought i was able to sftp files into the directory before using a normal user account created at install

---

### Post by Brazen on 2008-03-13
It should be owned by the www-data user.
It's probably also owned by the www-data group.  If you want to be able to write files to it, it would be much more secure to add yourself to the www-data group.  Then you should be able to write to it, although you might double-check the permissions (use "ls -l" in the parent folder).  They should be something like rwxrwxr-x.  It could also be rwxr-xr-x.  I don't remember what the default in Ubuntu is.  If it is the latter, you can do "sudo chmod -R 775 foldername" (plus add yourself to the owning group) and it would still be secure.

---

