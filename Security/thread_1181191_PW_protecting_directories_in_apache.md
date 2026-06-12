---
title: "PW protecting directories in apache"
date: 2009-06-07
forum: Security
---

### Post by Cyked on 2009-06-07
I'm trying to figure out how to make exclusions for directories.  Do I have to create another .htaccess file in the directory I want to have public access?  Does the directory I want to be public have to reside outside of the directory I have locked down?  

Here is what I have so far, and it works, but I'm not sure how to exclude a sub-directory from being PW protected.

.htaccess
```
AuthUserFile  /etc/apache2/passwd1/passwd2/.htpasswd
AuthType Basic
AuthName "Restricted Files"
Require valid-user

```

httpd.conf
```
<Directory /var/www/files>
AuthType Basic
AuthName "Restricted Files"
AuthUserFile /etc/apache2/passwd1/passwd2/
Require valid-user
</Directory>
```

I've tried adding lines for another directory to the httpd.conf file as an exclusion, but I haven't been able to make it work.

---

### Post by bodhi.zazen on 2009-06-07
separating public from private makes the most sense to me.

All you need to do is move the public files and directories out of the private.

If you have access to the server config file, you can put those directives right into the Apache config file rather then .htaccess.

[http://httpd.apache.org/docs/2.0/howto/auth.html](http://httpd.apache.org/docs/2.0/howto/auth.html)

---

### Post by Cyked on 2009-06-08
Thanks.  For some reason from what I had been reading I got the idea that I needed to put information into the httpd.conf file, but would only work if I was using .htaccess files.  I removed the .htaccess files and cleared the httpd.conf file and added what I had in the httpd.conf file to the apache config file.  

I still assume there are ways to make exceptions for sub-directories to allow access to all?

---

### Post by bodhi.zazen on 2009-06-08
Not that I know of, although I am not an apache expert.

---

### Post by Cyked on 2009-06-08
I'm playing around auth digest instead of basic but having issues creating the digest file and how to config the apache config file accordingly.  I must be doing something wrong with the htdigest command when I do htdigest -c  it tells me

```
Could not open passwd file -c for reading.
Use -c option to create new one.
```

To address the original issue I just moved the directories around so subdirectories are PW protected and others are not.  The dir I put protection on I renamed as .filename.

Thanks!

---

### Post by bodhi.zazen on 2009-06-08
My guess is you need to specify a user and password file

[http://httpd.apache.org/docs/2.0/programs/htdigest.html](http://httpd.apache.org/docs/2.0/programs/htdigest.html)

---

### Post by Cyked on 2009-06-08
That is what I am trying to do.  I think I'm screwing something up with the realm option.

---

### Post by bodhi.zazen on 2009-06-08
It might help if you were willing to post the exact command and the error message then ;)

---

