---
title: "problem with Wordpress on a web server"
date: 2008-08-18
forum: Server Platforms
---

### Post by raptor222 on 2008-08-18
Hi, i've set up a web server with wordpress and it works but when i'm editing a post and trying to upload an image i recive an error massage that the file could not be moved into the directory (after i created the upload directory manually).
i assume that the problem is wuth the user premissions, so i need to know how can ichange the user permissions so i will be able to upload files.

---

### Post by erwall on 2008-08-20
> **raptor222 said:**
> Hi, i've set up a web server with wordpress and it works but when i'm editing a post and trying to upload an image i recive an error massage that the file could not be moved into the directory (after i created the upload directory manually).
i assume that the problem is wuth the user premissions, so i need to know how can ichange the user permissions so i will be able to upload files.

try

```
sudo chown -R www-data. /var/www/wordpress
```

---

