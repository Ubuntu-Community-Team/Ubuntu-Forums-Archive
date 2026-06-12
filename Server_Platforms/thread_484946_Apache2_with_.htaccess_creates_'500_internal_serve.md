---
title: "Apache2 with .htaccess creates '500 internal server error'"
date: 2007-06-26
forum: Server Platforms
---

### Post by a.d.gardiner on 2007-06-26
Hey all,

Im having some teething problems with using  .htaccess and .htpasswd file's  on my apache2.

Basically I've set up both to guard one of my sites, which I'd like to password protect. In fact I got this to work just fine, but its an extra set of rules that protect against the 'Santy.A worm' which is causing my server to only display '500 internal server error'.

My htaccess looks like this:

```
AuthName "Restricted Area" 
AuthType Basic 
AuthUserFile /var/www/mysite/.htpasswd 
AuthGroupFile /dev/null 
require valid-user
RewriteEngine on

RewriteCond %{HTTP_REFERER} ^.*$
RewriteRule ^.*%27.*$ http://127.0.0.1/ [redirect,last]
RewriteRule ^.*%25.*$ http://127.0.0.1/ [redirect,last]
RewriteRule ^.*rush=.*$ http://127.0.0.1/ [redirect,last]
RewriteRule ^.*echr.*$ http://127.0.0.1/ [redirect,last]
RewriteRule ^.*esystem.*$ http://127.0.0.1/ [redirect,last]
RewriteRule ^.*wget.*$ http://127.0.0.1/ [redirect,last]

# prevent pre php 4.3.10 bug
RewriteCond %{HTTP_COOKIE}% s:(.*):\%22test1\%22\%3b
RewriteRule ^.*$ http://127.0.0.1/ [R,L]

# prevent perl user agent (most often used by santy)
RewriteCond %{HTTP_USER_AGENT} ^lwp.* [NC]
RewriteRule ^.*$ http://127.0.0.1/ [R,L]
RewriteCond %{HTTP_REFERER} ^.*$
```

As far as I'm aware this should just work? :-|

---

### Post by a.d.gardiner on 2007-06-26
If it's any use the error readout is:


> Internal Server Error

The server encountered an internal error or misconfiguration and was unable to complete your request.

Please contact the server administrator, [no address given] and inform them of the time the error occurred, and anything you might have done that may have caused the error.

More information about this error may be available in the server error log.

---

### Post by tr333 on 2007-06-26
> More information about this error may be available in the server error log.

Did you look at the error log?  I find looking at the log usually helps to diagnose problems.

```
$ less /var/log/apache2/error.log
```

---

