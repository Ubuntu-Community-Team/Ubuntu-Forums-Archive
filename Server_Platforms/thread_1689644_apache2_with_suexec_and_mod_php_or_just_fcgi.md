---
title: "apache2 with suexec and mod_php or just fcgi"
date: 2011-02-17
forum: Server Platforms
---

### Post by phazei on 2011-02-17
So, I can get mod_php, suexec, or just fcgi to all work on their own.

I'm trying to get either suexec/fcgi and non-suexec/fcgi working, or suexec and mod_php working.  I want it determinable per VirtualHost or Directory.

I can get it somewhat working.
For suexec + mod_php:
It seems mod_php takes the default.  If I go "php_admin_flag engine off" for a Directory, it doesn't kick in because "SetHandler application/x-httpd-php" is in the php5.conf folder.  If I comment it out, then it works.  But I want to overwrite that somehow.  Not sure why it doesn't fall back to the suexec once the php engine is off.

But I figured it might be better to do fcgi without the suexec so I'm not running two different php modules.  I can get it working one or the other, but I can't figure out how to enable or disable them if together.

Basically I have some sites I need to run under the users themselves, and also some other universal scripts that are Aliased that I want running everywhere without needing a install on for every single user.

Any ideas?


Oh, also, is there a way to have a single FCGIWrapper rather than needing one for every user?  I've seen it that way on other distros, not sure if it can be done here.

Thanks

---

### Post by phazei on 2011-02-17
Figures, I spend 8hours working on this, post a question, and make progress.

I still can't get suexec/fcgi and nosuexec/fcgi to work at the same time.  But I did get suexec and mod_php nearly there.

When I want suexec working without the mod_php I put this in the <Directory> tag:

        <IfModule mod_php5.c>
                php_admin_flag engine off
        </IfModule>
        <FilesMatch "\.ph(p3?|tml)$">
                SetHandler fcgid-script
        </FilesMatch>
        <IfModule mod_fcgid.c>
                Options +ExecCGI
                AddHandler fcgid-script .php
                FCGIWrapper /var/www/user/php-fcgi-starter .php
        </IfModule>

I have to have the SetHandler and AddHandler just like that or it doesn't work.  I tried having the SetHandler just above the AddHandler and it gave an error about the directory being forbidden.  [S]It will run index.php if the path just ends in the directory, but if I type index.php in it tries to download it still.....  so still can't get it.[/S]  Chrome was caching the download, fixed that and now it seems to be working.

But gitweb needs to run as a cgi script, so somehow I need to exclude it from using suexec and only use fcgi since it gives 500 errors.

---

### Post by phazei on 2011-02-18
Got it all working now.

working while not in web root:
mod_php -> phpmyadmin
mod_perl -> gitweb

fcgi/suexec as usual too.  Though I found it works for any symlink that's not in the web root too, but only with php, not cgi.

Here's some of my config settings:
```


[S]#mods-available/perl.conf[/S]

#conf.d/gitweb
Alias /gitweb /usr/share/gitweb

<Directory /usr/share/gitweb>
   PerlHandler ModPerl::Registry
   AddHandler perl-script .cgi
</Directory>

#sites-available/myuser
<VirtualHost *:80>
  ServerAdmin webmaster@example1.com
  DocumentRoot /var/www/myuser/

    <IfModule mod_suexec.c>
        SuexecUserGroup myuser myuser
    </IfModule>
    <Directory /var/www/myuser/>
        <IfModule mod_fcgid.c>
                <IfModule mod_php5.c>
                        php_admin_flag engine off
                </IfModule>
                <FilesMatch "\.ph(p3?|tml)$">
                        SetHandler fcgid-script
                </FilesMatch>
                Options +ExecCGI
                AddHandler fcgid-script .php
                FCGIWrapper /var/www/myuser/php-fcgi-starter .php
        </IfModule>
        AllowOverride All
        Order allow,deny
        Allow from all
    </Directory>

  ServerSignature Off

</VirtualHost>


```

Oh, and I'm using apache2-suexec-custom, though I haven't changed any of the default settings on it.

No clue how secure this is or how much it slows it running the extra apache mods, but it doesn't matter much since it's a dev box.

---

