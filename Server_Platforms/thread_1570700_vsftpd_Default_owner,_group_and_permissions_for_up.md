---
title: "vsftpd: Default owner, group and permissions for upload"
date: 2010-09-08
forum: Server Platforms
---

### Post by megabuffen on 2010-09-08
Hi.

I have set up a web server and I'm using vsftpd to handle file uploads.  The problem is, when i upload a new file both the owner and group for  the uploaded file is set to the user that is logged into the FTP server.  For example, when i log into FTP with my user account "kalle" and  create a file, the ownership is set to "kalle:kalle". I want to use the  current user as owner and www-data as group, which in my example means that the ownership would be "kalle:www-data".

Also, i want the permissions for the file to be 775, and i have set "local_umask=002" in "/etc/vsftpd.conf". As far as I understand, this would make the permissions 777-002=775, but it is instead set to 664.

The ownership and permissions of /var/www and all subfolders is "kalle:www-data" and 775.

Does anyone know how I can accomplish this?

---

### Post by ingramproductions on 2011-09-13
bump

---

### Post by zackwasa on 2011-09-14
For the ownership you will need to change the group of the kalle user to be www-data. You can do so using:
```

usermod -g www-data kalle

```

For default 755 permissions you need to set the local_umask option in vsftpd.conf to be 022

[FONT=monospace]**[/FONT]

---

### Post by johnhopkins on 2011-12-20
That's great. It works for me. Thanks.

---

