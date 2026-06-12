---
title: "/var/www permission question"
date: 2011-10-13
forum: Server Platforms
---

### Post by fouadk on 2011-10-13
hi everyone

i am wondering if the current user:group ownership of my /var/www is secure

i have proftpd server installed and i have added an ftp user to the www-data group via usermod -a -G www-data ftpuser

and then i have changed the ownership of /var/www to root:www-data

and then i have changed the flags of /var/www to 774

is that secure?

Thanks in advance

---

### Post by vasile002 on 2011-10-13
the most secure way to run things would be for /var/www to be owned by the FTP user only, all the files/dirs should have maximum 755 permissions and the apache/php should either run using suphp or fastcgi under the FTP user of /var/www/

I hope this answers your question

---

