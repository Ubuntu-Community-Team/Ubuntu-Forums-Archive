---
title: "apache2 403 error"
date: 2010-03-10
forum: Server Platforms
---

### Post by hockey97 on 2010-03-10
Hi, how would I fix this error?

I looked at my apache2 logs.

here is what they show in the error log: ```
[Wed Mar 10 01:56:34 2010] [crit] [client 192.168.1.100] (13)Permission denied: /home/user/.htaccess pcfg_openfile: unable to check htaccess file, ensure it is readable
```

the server is located at /etc/apache2 the default place. 

I don't know what to do.

how do I fix this?

---

### Post by Ryan Dwyer on 2010-03-10
The filesystem permissions on the .htaccess file prevent the web server from reading it.

Run ls -l /home/user/.htaccess to see who the owner is. Change the owner to your apache user (usually www-data) using sudo chown www-data.www-data /home/user/.htaccess.

---

