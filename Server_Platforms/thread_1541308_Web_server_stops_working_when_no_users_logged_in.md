---
title: "Web server stops working when no users logged in??"
date: 2010-07-29
forum: Server Platforms
---

### Post by flatline on 2010-07-29
I just noticed this issue, and I'm a little confused by it.  I have 10.04 server edition installed on my box.  I setup LAMP, but the only thing I have in /var/www is a symlink to my MyFolding.html page in my ~/folding/ directory, so I can monitor the progress of my folding from anywhere.  I had this exact same setup when I was running server 9.04 and it worked beautifully.  However, now it seems that the symlink only works when i am logged in locally or ssh'd into the box... if there are no user sessions logged in, the web server doesn't seem to work.  I get:
```

Forbidden

You don't have permission to access / on this server.
Apache/2.2.14 (Ubuntu) Server at my.dynamicDNS.account.net Port 8081
```

I put a sample "hello world" html file into /var/www and it worked ok.

I am thinking the culprit was when I tried to turn off directory listing.  Here is my /etc/apache2/ports.conf:
```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
NameVirtualHost *:8081
Listen 80
Listen 8081

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

```
And here is my /etc/apache2/sites-enabled/000-default
```
<VirtualHost *:80 *:8081>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog /var/log/apache2/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options -Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
</VirtualHost>
```

I have FollowSymLinks, so I'm not sure what I've missed.  Thanks!

---

### Post by flatline on 2010-07-29
In case someone really wants to see /var/apache2/error.log:
```
~$ tail /var/log/apache2/error.log
[Thu Jul 29 00:29:21 2010] [error] [client 108.3.203.56] Symbolic link not allowed or link target not accessible: /var/www/index.html
[Thu Jul 29 00:29:24 2010] [error] [client 108.3.203.56] Symbolic link not allowed or link target not accessible: /var/www/index.html
[Thu Jul 29 00:31:45 2010] [error] [client 108.3.203.56] Symbolic link not allowed or link target not accessible: /var/www/index.html
[Thu Jul 29 01:17:42 2010] [error] [client 108.3.203.56] Symbolic link not allowed or link target not accessible: /var/www/index.html
[Thu Jul 29 01:18:21 2010] [error] [client 108.3.203.56] File does not exist: /var/www/favicon.ico
[Thu Jul 29 01:18:24 2010] [error] [client 108.3.203.56] File does not exist: /var/www/favicon.ico
[Thu Jul 29 01:20:24 2010] [error] [client 108.3.203.56] Symbolic link not allowed or link target not accessible: /var/www/index.html
[Thu Jul 29 01:20:24 2010] [error] [client 108.3.203.56] Symbolic link not allowed or link target not accessible: /var/www/index.html
[Thu Jul 29 01:20:25 2010] [error] [client 108.3.203.56] Symbolic link not allowed or link target not accessible: /var/www/index.html
[Thu Jul 29 01:20:27 2010] [error] [client 108.3.203.56] Symbolic link not allowed or link target not accessible: /var/www/index.html

```

---

### Post by y@w on 2010-07-29
Is your home directory encrypted or something that would cause it to not be accessible when you're not logged in? Or maybe an NFS mount that got stuck in a .bashrc/.bash_profile file?

---

### Post by flatline on 2010-07-29
I think I've figured out my problem... when I installed 10.04, I opted for "encrypt /home directories"... I imagine that when I logout of my user session, it re-encrypts my ~/folding directory.  That would explain why it can't follow the symlink when I logout, the target is encrypted.  Does this sound like it might be the underlying problem?  My bigger question is, since my folding app is in ~/, does that mean that folding will stop when I log out of the server??

I am afraid my options are going to be A) reinstall the OS and NOT encrypt /home or B) move ~/folding to another directory.

edit: y@w beat me to it... is there a relatively painless way to turn-off home directory encryption once it has been enabled, that doesn't involve re-installing the OS?

---

### Post by flatline on 2010-07-29
Home directory encryption was definitely the issue.  I have moved my /folding directory to /home/folding, and this has alleviated the issue.  Symlinks don't randomly disappear now, and folding appears to be running uninterrupted.  Thanks y@w for confirming my suspicion.

---

