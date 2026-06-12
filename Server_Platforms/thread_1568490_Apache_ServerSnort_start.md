---
title: "Apache Server/Snort start"
date: 2010-09-05
forum: Server Platforms
---

### Post by iamgeniusrnti on 2010-09-05
Ok--I'm on the brink of getting Snort up and running and I'm stuck on the step regarding getting the Apache up and running.

```
genius@ubuntu-server:/var/www$ sudo /etc/init.d/apache2 start * Starting web server apache2                                                  Syntax error on line 3 of /etc/apache2/sites-enabled/000-default:
Invalid command '\xe2\x80\x82\xe2\x80\x82\xe2\x80\x82\xe2\x80\x82RewriteEngine', perhaps misspelled or defined by a module not included in the server configuration
```


Here is the beginning of the file it's complaining about:
```

<VirtualHost *:80>
<IfModule mod_rewrite.c>
&#8194;&#8194;&#8194;&#8194;RewriteEngine On
&#8194;&#8194;&#8194;&#8194;RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
&#8194;&#8194;&#8194;&#8194;RewriteRule .* - [F]
</IfModule>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options -Indexes FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```

And here is my tail of the syslog:

```

genius@ubuntu-server:/var/www$ tail /syslog
tail: cannot open `/syslog' for reading: No such file or directory
genius@ubuntu-server:/var/www$ tail /var/log/syslog
Sep  5 09:58:17 ubuntu-server gdm-simple-greeter[29008]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Sep  5 09:58:18 ubuntu-server gdm-simple-greeter[29008]: WARNING: Unable to write to login cache file: /var/lib/gdm/.cache/login_frequency.cache
Sep  5 09:58:21 ubuntu-server gdm-session-worker[29010]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Sep  5 09:58:26 ubuntu-server gnome-session[29027]: WARNING: GSIdleMonitor: IDLETIME counter not found
Sep  5 09:58:35 ubuntu-server pulseaudio[29081]: module-x11-bell.c: XkbQueryExtension() failed
Sep  5 09:58:35 ubuntu-server pulseaudio[29081]: module.c: Failed to load  module "module-x11-bell" (argument: "display=::ffff:127.0.0.1:1.0 sample=bell.ogg"): initialization failed.
Sep  5 10:00:01 ubuntu-server CRON[29183]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Sep  5 10:09:01 ubuntu-server CRON[29409]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep  5 10:17:01 ubuntu-server CRON[29750]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  5 10:20:01 ubuntu-server CRON[29842]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)

```


I'm not terrible experienced with web servers so this may be a silly question but I didn't know where to begin searching:S

---

### Post by arvindkst on 2012-08-18
replace <IfModule mod_rewrite.c> with <IfModule mod_rewrite>

---

### Post by sandyd on 2012-08-20
> **iamgeniusrnti said:**
> Ok--I'm on the brink of getting Snort up and running and I'm stuck on the step regarding getting the Apache up and running.

```
genius@ubuntu-server:/var/www$ sudo /etc/init.d/apache2 start * Starting web server apache2                                                  Syntax error on line 3 of /etc/apache2/sites-enabled/000-default:
Invalid command '\xe2\x80\x82\xe2\x80\x82\xe2\x80\x82\xe2\x80\x82RewriteEngine', perhaps misspelled or defined by a module not included in the server configuration
```
Here is the beginning of the file it's complaining about:
```

<VirtualHost *:80>
<IfModule mod_rewrite.c>
&#8194;&#8194;&#8194;&#8194;RewriteEngine On
&#8194;&#8194;&#8194;&#8194;RewriteCond %{REQUEST_METHOD} ^(TRACE|TRACK)
&#8194;&#8194;&#8194;&#8194;RewriteRule .* - [F]
</IfModule>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options -Indexes FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

```And here is my tail of the syslog:

```

genius@ubuntu-server:/var/www$ tail /syslog
tail: cannot open `/syslog' for reading: No such file or directory
genius@ubuntu-server:/var/www$ tail /var/log/syslog
Sep  5 09:58:17 ubuntu-server gdm-simple-greeter[29008]: Gtk-WARNING: /build/buildd/gtk+2.0-2.20.1/gtk/gtkwidget.c:5636: widget not within a GtkWindow
Sep  5 09:58:18 ubuntu-server gdm-simple-greeter[29008]: WARNING: Unable to write to login cache file: /var/lib/gdm/.cache/login_frequency.cache
Sep  5 09:58:21 ubuntu-server gdm-session-worker[29010]: GLib-GObject-CRITICAL: g_value_get_boolean: assertion `G_VALUE_HOLDS_BOOLEAN (value)' failed
Sep  5 09:58:26 ubuntu-server gnome-session[29027]: WARNING: GSIdleMonitor: IDLETIME counter not found
Sep  5 09:58:35 ubuntu-server pulseaudio[29081]: module-x11-bell.c: XkbQueryExtension() failed
Sep  5 09:58:35 ubuntu-server pulseaudio[29081]: module.c: Failed to load  module "module-x11-bell" (argument: "display=::ffff:127.0.0.1:1.0 sample=bell.ogg"): initialization failed.
Sep  5 10:00:01 ubuntu-server CRON[29183]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)
Sep  5 10:09:01 ubuntu-server CRON[29409]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Sep  5 10:17:01 ubuntu-server CRON[29750]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Sep  5 10:20:01 ubuntu-server CRON[29842]: (smmsp) CMD (test -x /etc/init.d/sendmail && /usr/share/sendmail/sendmail cron-msp)

```
I'm not terrible experienced with web servers so this may be a silly question but I didn't know where to begin searching:S
Reenter ALL the spaces in your config file.
In fact, use the backspace key to move
```
RewriteEngine On
```
up to the line
```
<IfModule mod_rewrite.c>
```
Then use enter and tab to put it in the original position

---

