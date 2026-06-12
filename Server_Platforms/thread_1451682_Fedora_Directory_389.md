---
title: "Fedora Directory 389"
date: 2010-04-10
forum: Server Platforms
---

### Post by quikone8 on 2010-04-10
I am almost finished with the installation of the Fedora 389 directory server but am getting this error; /etc/init.d/dirsrv-admin start
Starting dirsrv-admin: 
 * /var/run/dirsrv is not writable for 
ron@tolmarket:~$ 

Any idea how to overcome this?  I would assume it has to do with ownership, but I don't know how to fix it.

Ron

---

### Post by Skidbladnir on 2010-04-10
I'm not exactly sure about what user should own the file, but run
```

cat /etc/user

```
and you should be able to guess.  Then run:
```

chown -R user:group SpamEggs

```

The group is NORMALLY the same as the user.

---

