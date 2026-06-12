---
title: "web server global permissions"
date: 2009-05-15
forum: Server Platforms
---

### Post by k33bz on 2009-05-15
I am running a web server, that is running a wordpress site. I cant upload directly from my wordpress at the moment, or edit my config files from there either. I can do that all from my server directly via CLI, or if I ssh or sftp into it. But I need use of ease. I can find which files and directories on my own. Just need to know what the global permission command is, or maybe a different permission command that will give me what I want.

Basically permissions to access the webserver and change settings via HTTP with the websites ADMIN name and PW.

---

### Post by Kareeser on 2009-05-15
It is not advisable to give global permissions to the entire directory, as any compromised account could potentially bring down your wordpress blog.

For basic functionality, the wp-content/uploads folder needs to be writable by "www-data". 

```
sudo chown -R www-data:www-data /path/to/wp-content/uploads
```

The plugins directory can also be written to, if you so wish.

For general site configurations, wp-config.php needs to be writable by that user or group as well.

Do you understand U, G, and O permissions?

---

### Post by k33bz on 2009-05-17
> **Kareeser said:**
> It is not advisable to give global permissions to the entire directory, as any compromised account could potentially bring down your wordpress blog.

For basic functionality, the wp-content/uploads folder needs to be writable by "www-data". 

```
sudo chown -R www-data:www-data /path/to/wp-content/uploads
```

The plugins directory can also be written to, if you so wish.

For general site configurations, wp-config.php needs to be writable by that user or group as well.

Do you understand U, G, and O permissions?

Yes I understand U, G, and O permissions. Thanks

---

