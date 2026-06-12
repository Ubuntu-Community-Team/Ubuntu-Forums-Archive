---
title: "Using PAM authentication from PHP, can't change pw"
date: 2009-06-10
forum: Security
---

### Post by johnnybeem on 2009-06-10
Hi all,
I am working on setting up PAM authentication for my LAMP website. I downloaded [this]("http://pecl.php.net/package/PAM") PECL package, which works well for authentication purposes but when using it to change passwords I have been getting "Permission Denied". I think it is a problem with my PAM configuration.

Apache2 is running as www-data and I had to chgrp /etc/shadow to www-data, then make it group readable for the authentication to work.

Here is my /etc/pam.d/php file:
auth            sufficient      pam_unix.so shadow nodelay
account         sufficient      pam_unix.so
password        sufficient      pam_unix.so md5 debug

Here is the error returning from the pam_chpass function:
Permission denied (in pam_chauthtok)

And finally here are the related logs in /var/log/auth.log
Jun 10 10:21:50 HOSTNAME apache2: pam_unix(php:chauthtok): username [someusername] obtained
Jun 10 10:21:50 HOSTNAME apache2: pam_unix(php:chauthtok): conversation failed
Jun 10 10:21:50 HOSTNAME apache2: pam_unix(php:chauthtok): unable to obtain a password
Jun 10 10:21:50 HOSTNAME apache2: pam_unix(php:chauthtok): password - (old) token not obtained

Any suggestions??

Thanks

---

### Post by cdenley on 2009-06-10
> **johnnybeem said:**
> Hi all,
I am working on setting up PAM authentication for my LAMP website. I downloaded [this]("http://pecl.php.net/package/PAM") PECL package, which works well for authentication purposes but when using it to change passwords I have been getting "Permission Denied". I think it is a problem with my PAM configuration.

Apache2 is running as www-data and I had to chgrp /etc/shadow to www-data, then make it group readable for the authentication to work.

Here is my /etc/pam.d/php file:
auth            sufficient      pam_unix.so shadow nodelay
account         sufficient      pam_unix.so
password        sufficient      pam_unix.so md5 debug

Here is the error returning from the pam_chpass function:
Permission denied (in pam_chauthtok)

And finally here are the related logs in /var/log/auth.log
Jun 10 10:21:50 HOSTNAME apache2: pam_unix(php:chauthtok): username [someusername] obtained
Jun 10 10:21:50 HOSTNAME apache2: pam_unix(php:chauthtok): conversation failed
Jun 10 10:21:50 HOSTNAME apache2: pam_unix(php:chauthtok): unable to obtain a password
Jun 10 10:21:50 HOSTNAME apache2: pam_unix(php:chauthtok): password - (old) token not obtained

Any suggestions??

Thanks

If you had to make /etc/shadow readable for authentication to work, then you probably have to make it writeable to be able to change passwords or anything contained in that file.

---

### Post by johnnybeem on 2009-06-10
I tried setting /etc/shadow to 777 with the same error and logs...

---

### Post by johnnybeem on 2009-06-15
bump

---

### Post by johnnybeem on 2009-06-21
So nobody knows how to do this...

---

