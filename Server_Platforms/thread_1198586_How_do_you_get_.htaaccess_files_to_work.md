---
title: "How do you get .htaaccess files to work?"
date: 2009-06-27
forum: Server Platforms
---

### Post by cmoney12051 on 2009-06-27
I have installed ubuntu server 9.04 and have some files on my server that require the use of .htaccess files to work properly. do i need to enable them or something? How would i get the .htaccess files to work properly? thanks

---

### Post by TwiceOver on 2009-06-27
in your /etc/apache2/sites-enabled you'll find a configuration file for your virtual host.  Edit it and change "AllowOverrides None" to "AllowOverrides All"

---

### Post by cmoney12051 on 2009-06-27
when i try that i get this error

```
Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.
Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.1 with Suhosin-Patch Server at 10.0.0.6 Port 80
```

:(

---

### Post by credobyte on 2009-06-27
Execute:
```
a2enmode rewrite
```
And don't forget to check file permissions ( 644 ).

---

### Post by cmoney12051 on 2009-06-27
> Execute:
```
a2enmode rewrite
```

And don't forget to check file permissions ( 644 ). 

could you please explain that a bit more. thanks

---

### Post by TwiceOver on 2009-06-27
Unless I'm missing something rewrite has nothing to do with .hta files.

Make sure your "AllowOverride All" is just like that with the "A" capitalized.

---

### Post by cmoney12051 on 2009-06-27
I got it! i ran that sudo a2enmod rewrite and it worked!

---

### Post by ad_267 on 2009-06-27
Can you post the contents of your /etc/apache2/sites-available/default file, if that's the one you edited. (sites-enabled/000-default just symlinks to that)

Edit: Never mind, just saw you solved it.

---

