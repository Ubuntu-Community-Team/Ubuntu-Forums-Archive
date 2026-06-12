---
title: "How to solve this error"
date: 2010-12-23
forum: Server Platforms
---

### Post by mohan8653 on 2010-12-23
**Internal Server Error**

 The server encountered an internal error or misconfiguration and was unable to complete your request.
 Please contact the server administrator,  webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.
 More information about this error may be available in the server error log.
  Apache/2.2.16 (Ubuntu) Server at 192.168.1.4 Port 80

---

### Post by SeijiSensei on 2010-12-23
You probably have an Apache directive in the wrong place or perhaps it's misspelled.  

Did you look in /var/log/apache2/error.log as suggested?

---

### Post by furlabs on 2010-12-25
This is usually caused by conflicting instructions between your site conf and a .htaccess file. Check whether there is a file called .htaccess in that directory. You will need to use **ls -a** for it to show up.

If so, there may be an override in that file that your site conf is disallowing. Edit your site conf and put the following inside the Directory tag:
```
AllowOverride All
```
Then reload apache.
```
sudo apache2ctl graceful
```

---

### Post by mohan8653 on 2010-12-30
Thank  u

---

