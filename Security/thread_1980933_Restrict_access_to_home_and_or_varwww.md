---
title: "Restrict access to home and or /var/www"
date: 2012-05-16
forum: Security
---

### Post by stanthecat on 2012-05-16
Hi 

I'd like to set up a remote user that only has access to /var/www via ssh and sftp.

Is this possible ? I can use something like rbash to lock a user in to the home directory (which I can then usermod to /var/www) - But I also want a similar sort of control for a user when they sftp into my machine. In particular I don't want them to be able to view the directory structure.

I feel I'm close but I'm missing something with regard sftp.

Thanks

Stan

---

### Post by codemaniac on 2012-05-16
You can tweak the ftp configuration file to bar the user from wandering through different directories .
Edit vsftpd.conf , make sure **chroot_local_user=YES** entry is uncommented .

---

### Post by thnewguy on 2012-05-16
I think what you want is a chroot (jail) for SFTP connections. There is a tutorial on setting this up here:
[https://survivalguides.wordpress.com/2011/05/20/chroot-sftp-connection/](https://survivalguides.wordpress.com/2011/05/20/chroot-sftp-connection/)

Edit: this is probably a better explanation:
[http://www.debian-administration.org/articles/590](http://www.debian-administration.org/articles/590)

---

