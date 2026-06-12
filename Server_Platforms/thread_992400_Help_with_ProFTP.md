---
title: "Help with ProFTP?"
date: 2008-11-24
forum: Server Platforms
---

### Post by nightmare0 on 2008-11-24
I am having issues with my current ProFTP installation.
It seems everytime I login to my server through an ftp client it hangs for like 30 seconds at "waiting for welcome message..." is there anyway to eliminate this problem? I am thinking that it is because I haven't set a welcome message, but there is no way for me to check, cause I don't know how to set it. Help anyone?

---

### Post by nightmare0 on 2008-11-24
Oh, and I'm using ProFTPD 1.3.1 mysql database user setup on an Ubuntu 8.04.1 LTS Server

---

### Post by nightmare0 on 2008-11-24
*bump!*

---

### Post by trentscott4 on 2008-11-25
This is probably caused by a firewall or DNS timeout. By default ProFTPD will try to do both DNS and ident lookups against the incoming connection. If these are blocked or excessively delayed a slower than normal login will result.            

Your proftpd config is located at /etc/proftpd.conf.  To edit it, run ```
sudo vi /etc/proftpd.conf
``` from a terminal.  Hit 'Insert', and add these two lines:
```
UseReverseDNS off
IdentLookups                    off
```
Hit 'Esc' and type ':wq' to write/save the file and quit.  Finally restart proftpd after making the changes with ```
sudo /etc/init.d/proftpd restart
```

Let me know how that works! :)

---

### Post by cariboo on 2008-11-25
The UseReverseDNS off directive doesn't work with version 1.3.1, but 

> IdentLookups                    off

Stopped the wait for the welcome messages.

Thanks

JIm

---

