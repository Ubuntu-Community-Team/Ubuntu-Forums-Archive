---
title: "Apache 403 Errors With New Document Root"
date: 2012-02-26
forum: Server Platforms
---

### Post by gsilves30 on 2012-02-26
Hi,

I'm sure I'm doing something stupid here with ownership or permissions. I have an external drive in EXT4 mounted as /media/webdrive. I want to use this for my apache root as my main drive is a small SSD. Anyhow I have a virtual host set up in apache:

```
<VirtualHost *:80>
  ServerAdmin greg.silverstein@gmail.com
  ServerName fossbox.no-ip.org
  DocumentRoot /media/webdrive/www/
  ErrorLog /media/webdrive/logs/error.log
  CustomLog /media/webdrive/logs/access.log combined
  <Directory /media/webdrive/www>
     Options Indexes FollowSymlinks MultiViews
     AllowOverride None
     Order allow,deny
     allow from all
  </Directory>
</VirtualHost>
```

I have the www directory as 

drwxr-xr-x 2 ME     4096 2012-02-26 21:31 www

but when I try to access this (via local host or another computer) I'm getting  403. There is an index.html in the folder to test with.

Thanks in advance!

---

### Post by gsilves30 on 2012-02-26
Yup permissions silly. I had to change /media/webdrive not just /media/webdrive/www to everyone read.

---

