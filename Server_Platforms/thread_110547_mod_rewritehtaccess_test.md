---
title: "mod_rewrite/htaccess test?"
date: 2005-12-31
forum: Server Platforms
---

### Post by martz on 2005-12-31
Greetings,
  I'm trying to setup a server here at my home.  I installed apache2, php5 and mysql.  I enabled the mod_rewrite module (and phpinfo reports that it is indeed loaded), but any .htaccess file I use doesn't seem to work.  I've tried redirecting and regular renaming.  I've used both wordpress and manual changes to try getting it to work.  And I have AllowOverride All at the top of the .htaccess files.

An example htaccess file I was using for simple redirect:
```
AllowOverride All

RewriteEngine On
RewriteBase /
Redirect /test/ http://www.google.com
```

I read online that there is some kind of logging the mod_rewrite can do... but I can't figure out where to put the code to turn it on.  I'm also relatively new to linux, but I have made it the main operating system on my laptop, at least ofr the next month or so.  Is there any other way to test whether the urls are actually getting rewritten or anything that I can do to get this to work.  Thanks for anyhelp...

Matt

---

### Post by bahadir on 2005-12-31
[QUOTE=martz]  And I have AllowOverride All at the top of the .htaccess files.
[/QUOTE]
hi matt,

you need something like
```
<Directory /yourdocroot/*>
AllowOverride All
</Directory>
```
in your httpd-conf file... or the .htaccess will be ignored

> An example htaccess file I was using for simple redirect:
```
AllowOverride All

RewriteEngine On
RewriteBase /
Redirect /test/ http://www.google.com
```

This will not work...
Try 
```

RewriteEngine On
RewriteBase /
RewriteRule ^/test/ http://www.google.com [R]

```

> I read online that there is some kind of logging the mod_rewrite can do... but I can't figure out where to put the code to turn it on.  
Put 
```
RewriteLog /var/log/httpd/my_rewrite_log
RewriteLogLevel 3
```
in your http-conf file... 
LogLevel greater than 2 is only for debugging!!
> 
I'm also relatively new to linux, but I have made it the main operating system on my laptop, at least ofr the next month or so.  Is there any other way to test whether the urls are actually getting rewritten or anything that I can do to get this to work.  Thanks for anyhelp...

Matt

It's a good idea to read the [ rewrite guide]("http://httpd.apache.org/docs/2.0/misc/rewriteguide.html").

---

### Post by martz on 2005-12-31
I did read through the apache rewrite guide... and I did what you said... and it still doesn't seem to be working

I put this into  my httpd.conf file:
```
<Directory /*>
AllowOverride All
</Directory>
```

And then I put this in my .htaccess file:
```
RewriteEngine On
RewriteBase /
RewriteRule ^/ http://www.google.com [R]
```
Figuring that if I go just to the root folder, it should redirect to google  (I tried other variants... i.e. sending it to another directory like test before but those didn't work either)

Also... when I put the RewriteLog lines into httpd.conf and restart apache twice (the first time it does nothing) it says the second time... "httpd not running, trying to start"  and it says that each time thereafter, so I removed the lines and then it worked fine.

---

### Post by bahadir on 2006-01-06
[QUOTE=martz]

Also... when I put the RewriteLog lines into httpd.conf and restart apache twice (the first time it does nothing) it says the second time... "httpd not running, trying to start"  and it says that each time thereafter, so I removed the lines and then it worked fine.[/QUOTE]
Apache won't start if the log-directory does not exist or has not sufficient rights ..
Can you figure out, whether apache is reading your .htaccess file? (eg put some bogus lines in your .htaccess. This will provoke an internal server error, if .htaccess is inlcuded)

---

