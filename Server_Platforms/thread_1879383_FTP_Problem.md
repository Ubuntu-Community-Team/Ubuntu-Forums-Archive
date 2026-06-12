---
title: "FTP Problem"
date: 2011-11-11
forum: Server Platforms
---

### Post by Ben McKinlay on 2011-11-11
I have set up a Ubuntu 11.10 Server installation with a LAMP server and vsFTPd, SSH, and Bind 9.

I created the user "ftpadmin" with the home directory /var/www
I used chmod -R 777 /var/www and can upload files to /var/www

However, while uploading my forum, I accidentally uploaded the folder "phpBB3", which I need to delete, however it won't delete using FTP.

Does anyone know how to fix this?

---

### Post by Lars Noodén on 2011-11-11
chmod -R 777 opens up a big security hole.  To set the permissions back to what they where before for safe operation you can do the following:

```

sudo find /var/www -type d -exec chmod 755 {} \;
sudo find /var/www -type f -exec chmod 644 {} \;

```

If you want to, you can make a group (e.g. webmasters) and then assign that group to /var/www.

```

sudo groupadd webmasters
sudo chgrp -R webmasters /var/www
sudo find /var/www -type d -exec chmod 2775 {} \;
sudo find /var/www -type f -exec chmod 2664 {} \;

```

Then make yourself a member of that group.

Also, since you have SSH you [won't need FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/).  SSH supplies SFTP which is a secure replacement for FTP.  You can connect via SFTP using Filezilla or Nautilus.

---

### Post by Ben McKinlay on 2011-11-11
Unfortunately, I still cannot delete this folder, nor many other folder on my server in fact.

I can delete single files, and only some folders?

---

### Post by Lars Noodén on 2011-11-12
```

sudo rm -rfi /var/www/phpBB3

```

---

### Post by Ben McKinlay on 2011-11-12
Thanks. That fixed it :)

---

