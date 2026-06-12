---
title: "FTP Server to Apache2-root"
date: 2006-10-12
forum: Server Platforms
---

### Post by Nio on 2006-10-12
Hello,

I want to set up an ftp server and an account (with password).
This ftp server should access /var/www (apache2-root folder)
Permissions should be set correctly to www-data i guess so i can view the files in webbrowser in localhost.

Thanks in advance

---

### Post by michux on 2006-10-12
> **Nio said:**
> Hello,

I want to set up an ftp server and an account (with password).
This ftp server should access /var/www (apache2-root folder)
Permissions should be set correctly to www-data i guess so i can view the files in webbrowser in localhost.

Thanks in advance

1. Install proftpd:

```
apt-get install proftpd
```

2. FTP permissions work just like the filesystem permissions by default. The only thing you have to do is set up the required permissions for /var/www. For instance, if you want user "mike" to access the folder, add him to the www-data group.

3. Enjoy your new FTP server in Ubuntu :)

---

