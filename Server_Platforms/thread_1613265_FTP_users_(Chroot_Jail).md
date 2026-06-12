---
title: "FTP users (Chroot Jail)"
date: 2010-11-04
forum: Server Platforms
---

### Post by scumboss on 2010-11-04
Hi All

I work in a college and we wish to setup a web server for our students.  I need to allow the students to upload web work to their own folders and not be able to browse other folders.  I'm going to use Ubuntu Server.  What is the easiest way to allow this?  I've found something called Pure-FTPd, is this the preferred choice for doing this?

---

### Post by minaev on 2010-11-04
In vsftpd, this is done by uncommenting two lines in config:

```
# Uncomment this to allow local users to log in.
local_enable=YES
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
chroot_local_user=YES
```

---

### Post by scumboss on 2010-11-04
Thanks for that.  I've installed vsftpd and it works fine.  Users can upload files to their home directory.  I want users to be able to see the files they upload when they navigate to [http://somedomainname/testuser/](http://somedomainname/testuser/).  Do I need to create a directory called /var/www/testuser then bind it to /home/testuser?  Or is there any other way?

---

### Post by minaev on 2010-11-04
You can easily make users' home directories accessible via http, using Apache [per-user web directories]("http://httpd.apache.org/docs/2.0/howto/public_html.html").

---

