---
title: "Still .htaccess not working"
date: 2010-04-06
forum: Server Platforms
---

### Post by @mir on 2010-04-06
i have followed the tutorial from this site

[https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)

i have changed this file /etc/apache2/sites-available/default

and in this file i have changed **AllowOverride None** to **AllowOverride All**

but still i get 

[B]Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, webmaster@localhost and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.[/B]

Plz some one help i have installed and reinstalled apache 2 time already and now i am fedup 

plz help............ :(

---

### Post by lisati on 2010-04-06
Moved to "Server Platforms"

Did you remember to do this: ? ```
sudo /etc/init.d/apache2 reload
``` 

Any clues in the server log?

---

### Post by cdenley on 2010-04-06
```

tail /var/log/apache2/error.log

```
Where is the .htaccess file, and what are the permissions on it?

---

### Post by Pnuts on 2010-04-06
> **@mir said:**
> i have changed this file /etc/apache2/sites-available/default

and in this file i have changed **AllowOverride None** to **AllowOverride All**

At a super quick glance:

Did you do it in both places in the default file?

By default it is in there twice.

-Pnuts

---

### Post by @mir on 2010-04-07
> **Pnuts said:**
> At a super quick glance:

Did you do it in both places in the default file?

By default it is in there twice.

-Pnuts

Wait u mean default-ssl i have to change in that too

---

### Post by @mir on 2010-04-07
> **cdenley said:**
> ```

tail /var/log/apache2/error.log

```Where is the .htaccess file, and what are the permissions on it?


this is what i get when i write 

```
tail /var/log/apache2/error.log
```

```

[Wed Apr 07 00:52:05 2010] [notice] caught SIGTERM, shutting down
[Wed Apr 07 09:36:01 2010] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Wed Apr 07 09:48:29 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico, referer: http://localhost/test/bbb/123
[Wed Apr 07 10:00:39 2010] [notice] caught SIGTERM, shutting down
[Wed Apr 07 10:00:40 2010] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Wed Apr 07 10:00:54 2010] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Apr 07 10:00:54 2010] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.5 with Suhosin-Patch configured -- resuming normal operations
[Wed Apr 07 10:01:18 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico
[Wed Apr 07 10:01:21 2010] [error] [client 127.0.0.1] File does not exist: /var/www/favicon.ico


```

---

### Post by @mir on 2010-04-07
> **lisati said:**
> Moved to "Server Platforms"

Did you remember to do this: ? ```
sudo /etc/init.d/apache2 reload
```Any clues in the server log?


yes is did write this

```
sudo /etc/init.d/apache2 reload
```

and also this

```
sudo /etc/init.d/apache2 restart
```

---

### Post by s_ø on 2010-04-07
The AllowOverride directive is set twice in the default site.
In **<Directory />** it should be set to **AllowOverride None**
And  in **<Directory /var/www>** to **AllowOverride All**

You should only allow the overrides you need. If you only need to rewrite url use
**AllowOverride FileInfo**
If you also need autherization use
**AllowOverride FileInfo AuthConfig**

You need to post the error.log from when you get the internal server error.
If it says somthing about syntax error you need to check your .htaccess syntax.

---

### Post by @mir on 2010-04-08
Thankx guys 

i just restarted my system it started to work

;)

---

