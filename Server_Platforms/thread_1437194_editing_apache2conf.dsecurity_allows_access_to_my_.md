---
title: "editing /apache2/conf.d/security allows access to my entire filesystem"
date: 2010-03-23
forum: Server Platforms
---

### Post by MechaMechanism on 2010-03-23
When I edit the security file in /apache2/conf.d/ apache2 then allows access to my entire filesystem.  After edit I can access things like .org/docs, .org/icons, .org/boot.  I took my server offline for now.  All I want is to limit everything to /var/www/, with no sub dir in /www/.  I don't need stuff like cgi or php etc.  Even JavaScript I don't need.  All I'm looking for is plain html 4.  Basically locking it down nice and tight.

This is the part I'm trying to edit...

# Disable access to the entire file system except for the directories that
# are explicitly allowed later.
#
# This currently breaks the configurations that come with some web application
# Debian packages. It will be made the default for the release after lenny.
#
<Directory />
    AllowOverride None
    Order Deny,Allow
    Deny from all
</Directory>

---

### Post by cdenley on 2010-03-23
You have no php support unless you installed the PHP module. Javascript is client-side code, so that is completely unrelated to server configuration. The file you want to edit is /etc/apache2/sites-available/default. To disable CGI, comment out this part:
```

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

```
although it really doesn't matter if you don't have any CGI scripts installed. To prevent access to subdirectories which for whatever reason you created in /var/www even though you don't want them accessible, add this within the VirtualHost tag:
```

        <Directory /var/www/*/>
                AllowOverride none
                Order deny,allow
                Deny from all
        </Directory>

```
I think that will work. I haven't tested it. Sort of an odd requirement. If you don't want directories to be accessible, don't put them in /var/www.

---

### Post by koenn on 2010-03-23
Read the comments. 

> 
# Disable access to the entire file system except for the directories that
# are explicitly allowed later.

So you do not touch that section if you want to disable access to the entire file system, which is what you want.

You add additional config (in this file, or, preferably, in files under sites-available  with links from sites-enabled) where you eg. set /var/www as document root for your website, and manage access to it there.

---

### Post by MechaMechanism on 2010-03-25
Awesome, thanks very much for the clarification.  Much appreciated.  :D

---

