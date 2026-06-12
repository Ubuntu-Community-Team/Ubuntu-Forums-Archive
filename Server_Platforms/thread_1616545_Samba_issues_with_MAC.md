---
title: "Samba issues with MAC"
date: 2010-11-08
forum: Server Platforms
---

### Post by djanie78 on 2010-11-08
For weeks i have had issues with file permissions. Samba share being accessed by other users. finally sorted using umask and putting entries in the samba config. (I have users who ssh into the system as well hence the umask option)Works great... at least i thought it did untill i got complains regarding MAC users. Directories created via Mac users have a group r+x where as windows and ubuntu have group rwx which is how i set it up. So the obvious. Users are not able to write into directories created via Mac users. :confused:Anyone had this issue before?

---

### Post by djanie78 on 2010-11-08
any help please????

---

### Post by dtfinch on 2010-11-08
I haven't worked with mac clients, but you should be able to prevent them from reducing permissions on files or directories like any other client.

There's the "force create mode" and "force directory create mode" options to raise the minimum permissions on new files or directories. There's also "force security mode" and "force directory security mode" options to do the same when modifying permissions on existing files.

[http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#FORCECREATEMODE](http://www.samba.org/samba/docs/man/manpages-3/smb.conf.5.html#FORCECREATEMODE)

I've usually taken a lazier route and set "force user" to bypass file/directory security altogether and just rely on per-share security. But you'd lose the ability to see who created which files that way.

---

### Post by djanie78 on 2010-11-12
```
unix extensions = no
```

This is set in the samba config file, global section
that did the trick. This way Mac users will use the default umask set on the server just like everyone else. Mac users aint that special after all. :guitar:

---

