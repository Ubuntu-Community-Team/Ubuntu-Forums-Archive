---
title: "Apache 2 Document Root"
date: 2008-01-30
forum: Server Platforms
---

### Post by monkey56657 on 2008-01-30
Hello!

I used to be able to do this easy peasy but I just cant figure this out today...

Basically I have installed apache2, php5, mysql and both 3 seems to work but the problem lies in changing the DocumentRoot for just the default (any) host. I changed the file @ /etc/apache2/sites-available/default and filled in the values for DocumentRoot and the same in the <Directory ....> part. 

I have restarted the apache server several times and tried the "restart" and "reload" commands and even restarted the PC but still the document root actually comes up as /var/www/ as if its just ignored by changes. 

Any ideas on what im missing ?

Thanks in advance.

---

### Post by monkey56657 on 2008-01-30
Ive got a feeling it might not be getting anything from /etc/apache2/ as I changed the server root in apache2.conf and it had no effect on the servers ability to load.

---

### Post by monkey56657 on 2008-01-30
Okay thats done...

Why cant I run apache under my user account. I have to sudo it to get it just to run?

(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80

Is the error when run as my user...

---

### Post by MJN on 2008-01-31
All 'well known' ports (0-1023) require root/administrative privileges to bind to.
 
Mathew

---

