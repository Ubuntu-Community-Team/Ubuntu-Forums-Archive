---
title: "[SOLVED] trailing slash rewrite rule not working"
date: 2007-10-24
forum: Server Platforms
---

### Post by twistedtwig on 2007-10-24
Hi all,

I think I am probably doing something silly.  I have the following virtual host:

```
<VirtualHost *>
ServerName houseofhawkins.com
ServerAlias www.houseofhawkins.com
ServerAdmin jonadmin@houseofhawkins.com
DocumentRoot /var/www/root
<Directory />
Options FollowSymLinks +ExecCGI
AllowOverride all
</Directory>

#display error page if we get 502 error
ErrorDocument 502 /error.html
#if we get 503 unavailable give out different page
ErrorDocument 503 /sitedown.html
#display error page for error 404 page not found
ErrorDocument 404 /404.php

ErrorLog /var/log/apache2/error.log

#Possible values include: debug, info, notice, warn, error, crit, alert, emerg
logLevel warn
CustomLog /var/log/apache2/access.log combined
ServerSignature On

 RewriteEngine on
 RewriteLog "/var/log/apache2/rewrite_log"
 RewriteRule ^/sitemap.xml$ /sitemapxml.php
 RewriteRule ^/sitemap.html$ /sitemaphtml.php
 RewriteRule ^/projects/testarea/ /projects/testarea

ProxyRequests Off

<Proxy *>
  Order deny,allow
  Deny from all
</Proxy>

ProxyPass        /projects/testarea/ http://192.168.10.100/testArea/
ProxyPassReverse /projects/testarea/ http://192.168.10.100/testArea/

ProxyPass        /projects/cs_jawbreaker/ http://192.168.10.100/cs_jawbreaker/
ProxyPassReverse /projects/cs_jawbreaker/ http://192.168.10.100/cs_jawbreaker/

ProxyPass        /projects/holdem/ http://192.168.10.100/holdem/
ProxyPassReverse /proejcts/holdem/ http://192.168.10.100/holdem/

ProxyPass        /projects/tardis/ http://192.168.10.100/Tardis/
ProxyPassReverse /projects/tardis/ http://192.168.10.100/Tardis/

</VirtualHost>

```

the problem is this  RewriteRule ^/projects/testarea/ /projects/testarea rule is not working... do I have to do something else?  The other rules all work.. is it because they are in the root directory and this one is not? 

Thank you.. wish I understood this more

---

### Post by twistedtwig on 2007-10-25
Thought I had had a moment of insirpartion this morning... 

I tried : RewriteRule ^/projects/testarea/$ /projects/testarea [R]

I thought that the [R] might be needed to force the browser to refresh to get the new URL but to no avail.

---

### Post by MJN on 2007-10-25
What exactly is it you're trying to do? It looks to be working from here - requests for /projects/testarea/ get redirected (rewritten) to /projects/testarea (the file of which does not exist).
 
Maybe give an example of what a visitor might type in, and what you want doing with that URL (I can kind of guess given your proxypass layout but rather than me misunderstand it's better coming from you).
 
Mathew

---

### Post by twistedtwig on 2007-10-25
OH!!! hehe have a done it back to front?!?!?!?!?

i am trying to fix the trailing slash issue.. projects/testarea/ is s proxy to another server.. I want /projects/testarea to redirect to /projects/testarea/ to avoid file not found.

will investigate further as soon as I get home!

<--- possible numpty

---

### Post by bunker on 2007-10-25
Here is the generic way to add a trailing slash to any directory:

```
RewriteCond  %{REQUEST_FILENAME} -d
RewriteRule ^(.*?[^/])$          $1/ [L,R]
```

If you wanted to be pedantic, there's another way to do it without doing a test to see if it's a directory (in order to be faster) but I can't remember it.  This will likely suffice anyway.

---

### Post by twistedtwig on 2007-10-25
cool thank you very much!!!

just to confirm that I was being a numpty.. I had the logic in my head backwards:

 RewriteRule ^/projects/testarea$ /projects/testarea/ [R]

works like a charm.

Thanks Mathew once again :)

---

