---
title: "how upload big mysql database"
date: 2014-12-13
forum: Server Platforms
---

### Post by niki85 on 2014-12-13
Hello,

I try to upload mysql database 500mb on my server, but show me some limit error,
How i can add ''unlimited'' and can upload all possible sizes of mysql databases ?

Thanks.

---

### Post by volkswagner on 2014-12-14
How are you trying to upload, via phpmyadmin?

Something that large, I'd suggest using ssh/scp to upload, then use mysql command line (mysqldump)
to add/restore the database.

If you are using phpmyadmin, the upload limit is set in your php.ini file
To find your current limit:
```
sudo less /etc/php5/apache2/php.ini | grep "upload_max_filesize"
```

The above returns the following for me:

```
upload_max_filesize = 5M
```

Again you can edit the php.ini file and increase the size, but I suggest using scp to upload
the file to the server.

---

### Post by nerdtron on 2014-12-14
Is this a .sql file? If you have the option to SSH/SCP on the server, you can copy the file to the server first then you can just import from there.

---

