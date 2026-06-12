---
title: "DAV and .htaccess"
date: 2008-12-24
forum: Server Platforms
---

### Post by free-radical on 2008-12-24
Hi.

i try to configure apache2. it shall serve a directory with DAV, shall make user authentication via mysql and authorization via a set of ".htaccess" files, which are distributed in the directory tree which is to serve.

my apache2.conf contains this:

```

LoadModule mime_module			 /usr/lib/apache2/modules/mod_mime.so
LoadModule authz_host_module		 /usr/lib/apache2/modules/mod_authz_host.so
LoadModule dir_module			 /usr/lib/apache2/modules/mod_dir.so
LoadModule auth_basic_module		 /usr/lib/apache2/modules/mod_auth_basic.so
LoadModule authn_file_module		 /usr/lib/apache2/modules/mod_authn_file.so
LoadModule alias_module			 /usr/lib/apache2/modules/mod_alias.so
LoadModule cgi_module			 /usr/lib/apache2/modules/mod_cgi.so
LoadModule ssl_module			 /usr/lib/apache2/modules/mod_ssl.so
LoadModule php5_module			 /usr/lib/apache2/modules/libphp5.so
LoadModule rewrite_module		 /usr/lib/apache2/modules/mod_rewrite.so
LoadModule proxy_module			 /usr/lib/apache2/modules/mod_proxy.so
LoadModule auth_mysql_module		 /usr/lib/apache2/modules/mod_auth_mysql.so
LoadModule dav_module			 /usr/lib/apache2/modules/mod_dav.so
LoadModule dav_fs_module		 /usr/lib/apache2/modules/mod_dav_fs.so
LoadModule dav_svn_module		 /usr/lib/apache2/modules/mod_dav_svn.so
LoadModule authz_svn_module		 /usr/lib/apache2/modules/mod_authz_svn.so

...

#prevent access on .htaccess and .htpasswd from web
<FilesMatch "^\.ht">
    Order allow,deny
    Deny from all
</FilesMatch>
...
# default directory configuration. nothing allowed.
<Directory />
	Order Deny,Allow
	Deny from all
	Options FollowSymLinks
	AllowOverride None
</Directory>
...
Listen 8090
<VirtualHost *:8090>
    DocumentRoot /data/webdav
    DavLockDB /data/apache_stuff/davlock
    <Directory /data/webdav/>
	DAV On
	Options Indexes MultiViews
	Order Allow,Deny
	Allow From all
	AllowOverride All
    </Directory>
    <Location />
        AuthBasicAuthoritative Off
        AuthUserFile /dev/null
        AuthMySQL On
        AuthName "fr-webdav"
        AuthType Basic
        Auth_MySQL_Host XXX
        AuthMySQL_User XXX
        Auth_MySQL_Password XXX
        AuthMySQL_DB XXX
        AuthMySQL_Password_Table XXX
        Auth_MySQL_Username_Field XXX
        Auth_MySQL_Password_Field XXX
        Auth_MySQL_Empty_Passwords Off
        Auth_MySQL_Encryption_Types XXX
	Auth_MySQL_Authoritative On
	Auth_MySQL_Password_Clause XXX
        require valid-user
    </Location>
    SSLEngine on
</VirtualHost>

```

furthermore, my .htaccess files are as simple as that
```

Require user foo,bar,baz

```

Now, Apache uses my .htaccess files (when i write garbage in it, it complains about an internal server error), but it ignores the require argument completely. all my subdirectories are fully accessible with all valid users and not only for the users foo,bar,baz as defined. :confused:

Some ideas?


Thanks in advance

---

### Post by free-radical on 2009-01-04
Nobody with an idea or a small hint?

Can anybody say me, whether this is the normal behaviour or this in somewhat unusual?

---

