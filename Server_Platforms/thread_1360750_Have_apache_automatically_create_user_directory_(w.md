---
title: "Have apache automatically create user directory (webdav, mod_rewrite, ldap)"
date: 2009-12-21
forum: Server Platforms
---

### Post by Litachao on 2009-12-21
Hello all,

I have been trying my hands on Apache and WebDav. User authentication works through ldap, users are locked into their own webdav directory with mod_rewrite. This setup works so far, but the user-specific webdav directory needs to be in place before a user logs on for the first time, otherwise she'll get a "404 - not found".

**Is there any way to have apache check if the user-specific directory exists and to have it create that directory if it doesn't?**

Hope this is the right place to ask. I'm not much of a linux specialist and the below config has been patched together from various how-to's - but it works so far.

```

<VirtualHost 99.99.99.99:8080>
  #Basics 
  DocumentRoot /var/www/webdav/files
  DirectoryIndex index.php
  ServerName files.example.net
  ServerAlias files.*
  ServerAdmin www@example.net
  #
  #Enable SSL 
  SSLEngine On
  SSLCertificateFile /etc/ssl/certs/example.net.crt
  SSLCertificateKeyFile /etc/ssl/private/example.net.key 
  SSLCertificateChainFile /etc/ssl/certs/cacert.org.crt
  #
  #use mod-rewrite to lock users into their own webdav dir
  RewriteEngine On
  RewriteRule ^/(.*) /var/www/webdav/files/%{LA-U:REMOTE_USER}/$1
  #
  # define DAVLock location 
 <IfModule mod_dav_fs.c>
         DavLockDB /var/lib/apache2/DAVLock
 </IfModule>

<Directory /var/www/webdav/files>
      #enable webdav
      DAV On
      ForceType text/plain
      Options Indexes MultiViews
      AllowOverride None
      Order allow,deny
      Allow from all
     #
        # Authentication via LDAP
        AuthName "Please authenticate with your_email@example.net"
        AuthType Basic
        AuthBasicProvider ldap
        AuthzLDAPAuthoritative off
        AuthLDAPUrl "ldap://localhost/o=domains,dc=example,dc=net?mail"
        AuthLDAPBindDN "cn=someadmin,dc=example,dc=net"
        AuthLDAPBindPassword "*supersecretpwd*"
        require valid-user
        #
</Directory>
</VirtualHost>

```

---

### Post by Litachao on 2010-01-07
Alternatively, is there a way to have ldap create a directory (other than the $home directory) when a new user is added?

---

### Post by beniwtv on 2010-01-07
I have not seen any module for this. However, supposing that Apache has the rights to actually create such a directory by itself, you could make a rewrite rule that tests if the given directory exists, and if not, pass it to a PHP/CGI/Whatever script to create this directory.

Some example threads I found: 
[http://forums.devshed.com/apache-development-15/do-something-different-if-one-directory-exists-turn-off-re-writing-626439.html](http://forums.devshed.com/apache-development-15/do-something-different-if-one-directory-exists-turn-off-re-writing-626439.html)
[http://forums.devshed.com/apache-development-15/do-something-different-if-one-directory-exists-turn-off-re-writing-626439.html](http://forums.devshed.com/apache-development-15/do-something-different-if-one-directory-exists-turn-off-re-writing-626439.html)
[http://forum.lighttpd.net/topic/275](http://forum.lighttpd.net/topic/275)

Another idea would be to make a script on your server that creates those users in LDAP for you, and also creates all the necessary directories (or copy /etc/skel) when the user is created. That way, the user can log in the first time fine.

Or another idea is to use PAM to authenticate in Apache, and use the LDAP and mk_homedir modules for PAM. But that might not be what you want (this will allow to configure other services for LDAP as well, like E-mail, FTP, SSH and so on.

These are by no means complete tested solutions, only ideas, but might get you started. BTW the PAM-LDAP idea works fine as I use it :)

Cheers,

---

### Post by Litachao on 2010-01-13
Thank you!

---

