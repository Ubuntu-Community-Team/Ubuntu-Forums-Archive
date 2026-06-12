---
title: "Apache Permission errors?"
date: 2008-01-28
forum: Server Platforms
---

### Post by xelapond on 2008-01-28
Hello, 

I am trying to run a document magament system on my Ubuntu server.  I got Knowledgetree working and everything, except when I try to set it up it gives me a permission error:

> 
Error

Error type
    Failed to create log file /var/www/knowledgeTree-OSS/var/log/log-2008-01-28.www-data.txt (check permissions) 

How do I give it permissions to make the logfile?  Or can I just make it not use a logfile?

Thanks,

Alex

Also, security is not really an issue on this, its my home server with nothing important on it.

---

### Post by CheShA on 2008-01-28
what command did you run to get this message? Did you try  *sudo*ing it?

---

### Post by xelapond on 2008-01-28
Sorry, I forgot to mention that this happens when I go to *[www.example.com](www.example.com)*  Not when I run any command.

---

### Post by jpeddicord on 2008-01-28
(Moved to Servers & Security)

Most likely the permissions or uid/gid are not set correctly on /var/www/knowledgeTree-OSS/var/log/.

```
sudo chown www-data:www-data /var/www/knowledgeTree-OSS/var/log/
```Your logging directory appears to be a bit off, as logs are normally placed in /var/log/apache2. Did you change any defaults?

---

### Post by xelapond on 2008-01-28
Thanks, now it brings me to the log in page, as well as a bunch of other errors.

Above the login box it displays all of  this:

> Warning: mkdir() [function.mkdir]: Permission denied in /var/www/lib/cache/cache.inc.php on line 68

Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /var/www/lib/cache/cache.inc.php:68) in /var/www/lib/session/Session.inc on line 183

Warning: Cannot modify header information - headers already sent by (output started at /var/www/lib/cache/cache.inc.php:68) in /var/www/lib/session/Session.inc on line 184

Warning: Cannot modify header information - headers already sent by (output started at /var/www/lib/cache/cache.inc.php:68) in /var/www/lib/session/Session.inc on line 185

Warning: Cannot modify header information - headers already sent by (output started at /var/www/lib/cache/cache.inc.php:68) in /var/www/login.php on line 127

Any ideas?

Thanks, 

Alex

---

### Post by jpeddicord on 2008-01-28
> **xelapond said:**
> Thanks, now it brings me to the log in page, as well as a bunch of other errors.Hmm.. seems to be the same problem. Might as well chown the whole directory recursively:

```
sudo chown -R www-data:www-data /var/www
```If you are unable to edit any files after this as a result, you may have to edit them as root. (If you haven't been doing so already.)

---

