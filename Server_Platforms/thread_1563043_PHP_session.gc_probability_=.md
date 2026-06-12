---
title: "PHP session.gc_probability = ?"
date: 2010-08-28
forum: Server Platforms
---

### Post by DustWolf on 2010-08-28
Hello,

I have been noticing a bug in one of my websites that reads as:

ERROR 8: session_start() [function.session-start]: ps_files_cleanup_dir: opendir(/var/lib/php5) failed: Permission denied (13)
0 Error occurred on in function session_start
1 called from line 333 of file session.php in function require_once

Now... if I look this up on Google, I get an old post about this:
[http://somethingemporium.com/2007/06/obscure-error-with-php5-on-debian-ubuntu-session-phpini-garbage](http://somethingemporium.com/2007/06/obscure-error-with-php5-on-debian-ubuntu-session-phpini-garbage)
...which in short tells me that something unDebian is sitting in my php.ini and I need to set session.gc_probability back to 0, because the usual function won't work due to file permission restrictions and that a crontab is in place to do the cleanup for me.

The thing is, on my Ubuntu Server 10.04 AMD64, session.gc_probability is clearly set to 1. I have checked with a friend who has a fresh, clean install and his session.gc_probability is also set to 1. Yet the file permissions are still set restrictively and the crontab is right there! :confused:

I have set the session.gc_probability to 0 to get rid of the error, but I am not sure if there is something wrong with this setting or not? Should I file a bug report that session.gc_probability is configured incorrectly? Was the file permissions problem somehow overcome in Ubuntu? Did somebody unknowingly set this setting the wrong way in Ubuntu because the error pops up only with a very low probability?

Help?

LP,
Jure

---

### Post by Ryan Dwyer on 2010-08-28
Here are some related config options from my php.ini. Compare them with yours, especially the directory permissions.

session.gc_probability = 1
session.gc_divisor = 1000
session.save_path is commented, by phpinfo() shows it's defaulting to /var/lib/php5

ls -l /var/lib | grep php5
drwx-wx-wt  2 root          root          4096 2010-08-28 13:39 php5

---

### Post by DustWolf on 2010-08-28
> **Ryan Dwyer said:**
> Here are some related config options from my php.ini. Compare them with yours, especially the directory permissions.

session.gc_probability = 1
session.gc_divisor = 1000
session.save_path is commented, by phpinfo() shows it's defaulting to /var/lib/php5

ls -l /var/lib | grep php5
drwx-wx-wt  2 root          root          4096 2010-08-28 13:39 php5

[quote=Website from 2007]In Debian and Ubuntu, /var/lib/php5, where the session data is stored, has permissions of drwx-wx-wt and should only be cleaned by a cron script. So, the package maintainers disable automatic session garbage collection.[/quote]

According to this, your setting is wrong. 

Note however that according to your settings, your sites only encounter the error once per 1000 session starts, if these occur in under 30 minutes.

LP,
Jure

---

