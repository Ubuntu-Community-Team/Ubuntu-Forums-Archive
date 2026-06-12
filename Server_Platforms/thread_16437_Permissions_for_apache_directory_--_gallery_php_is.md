---
title: "Permissions for apache directory -- gallery php issue"
date: 2005-02-21
forum: Server Platforms
---

### Post by Stephen-I-M on 2005-02-21
A couple of questions: who should be the owner and group of files in /var/www?

I'm getting the dreaded "Could not open lock file" error using gallery. I heard that this could be fixed by setting the permissions on the album directory to 777. That doesn't sound like a good idea to me. Is there a better way?

Stephen

---

### Post by cpinto on 2005-02-21
do this as root or with sudo:

chown -R www-data:www-data /var/www 

and you should be good to go

---

### Post by Stephen-I-M on 2005-02-21
Thanks!  -- Stephen

---

