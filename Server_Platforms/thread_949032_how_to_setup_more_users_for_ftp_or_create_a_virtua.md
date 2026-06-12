---
title: "how to setup more users for ftp or create a virtual ftp host"
date: 2008-10-15
forum: Server Platforms
---

### Post by kustomjs on 2008-10-15
Hi Guys
I just wanted to know how can I setup one more user to my proftpd server or how to setup a virtual ftp host.

---

### Post by forger on 2008-10-15
have you tried [gadmin-proftpd]("apt://gadmin-proftpd") ?


> Description: GTK+ configuration tool for proftpd
 gadmin-proftpd is a fast and easy to use GTK+ administration tool for the
 Proftpd standalone server.
 .
 gadmin-proftpd gives admins easy access to virtual hosting, 8 layers of
 security including chrooted users and encrypted transfers on both the data
 and/or control channels.
Homepage: [http://www.gadmintools.org/](http://www.gadmintools.org/)

also read this:
[https://help.ubuntu.com/community/ProFTPD](https://help.ubuntu.com/community/ProFTPD)

---

### Post by kustomjs on 2008-10-15
I only have is command line only and I use putty to install stuff and do everything for my server and i use webmin also.

---

### Post by forger on 2008-10-15
in that case, I can only point you to some links:
[http://www.proftpd.org/docs/howto/index.html](http://www.proftpd.org/docs/howto/index.html)
[http://www.proftpd.org/docs/howto/ConfigFile.html](http://www.proftpd.org/docs/howto/ConfigFile.html)
[http://www.proftpd.org/docs/howto/Vhost.html](http://www.proftpd.org/docs/howto/Vhost.html)

---

### Post by lykwydchykyn on 2008-10-16
By default proftpd just uses system users, so you can add another system user.  I'm not aware of whether or not it can create "virtual users", but you don't have to give the user a valid logon shell (in case you want to let them ftp but not ssh or otherwise log in).

webmin's proftpd interface is pretty straightforward.  If you want to make a virtual host, you just need to decide how you want to differentiate it from the default -- different name, ip, or port.

---

