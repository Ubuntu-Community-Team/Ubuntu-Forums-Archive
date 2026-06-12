---
title: "Web Server/FTP Server + Permissions?"
date: 2006-12-04
forum: Server Platforms
---

### Post by SilverTab on 2006-12-04
Hi there! 

I just successfully installed lighttpd + php5-cgi + mysql

Everything seems to be working, by DocumentRoot is:
/var/www


Now what I want to do is to setup an FTP server to be able to upload/delete/rename etc in /var/www

I installed proftpd, its working, but Im not so sure how I can add a user with those permissions on /var/www ??

I tried creating a new user and setting it's group to www-data  but I still can't upload or anything with it via ftp???

What am I missing here?

---

### Post by SilverTab on 2006-12-04
Well here is how I solved the problem

Created a new user in the www-data group and set its home to /var/www

```

adduser --home /var/www --ingroup www-data silvertab

```

Then I set the permissions of /var/www to 775 recursively, so the www-data group can upload/delete in it
```

chmod -R 775 www

```

then I changed the group of all files in /var/www to www-data
```

chgrp -R www-data /var/www

```


No idea if it's how it should be done but it's working! If someone has a more secure/efficient way, please let me know!

---

