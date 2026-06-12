---
title: "Simple File Permission Problem in /var/www"
date: 2011-04-22
forum: Server Platforms
---

### Post by MikeMTM on 2011-04-22
I am in the www-data group...
```

mike@webserver:/var/www$ groups mike
mike : www-data adm dialout cdrom plugdev lpadmin sambashare admin

```

when I run ls...

```
mike@webserver:/var/www$ ls -la
total 8
drwxrwxr-x  2 www-data www-data 4096 2011-04-22 09:30 .
drwxr-xr-x 14 root     root     4096 2011-04-20 18:22 ..
-rw-r--r--  1 root     root        0 2011-04-22 09:24 index.html
```

I assumed that means that the users in the www-data group can read, write and execute within this folder?

But when I try to create a new file/dir I get permission denied message.

I'm having fun messing around with my new LAMP server, but this problem is annoying me now :).

Any help would be great, thanks.


(Oh and the index.html file was created by root, it's a blank file and can be deleted)

---

### Post by MikeMTM on 2011-04-22
OK, now it's working?

What happened?

Oh well, as long as it's working.

:oops::redface::oops:

---

