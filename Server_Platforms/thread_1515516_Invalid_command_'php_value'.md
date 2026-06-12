---
title: "Invalid command 'php_value'"
date: 2010-06-22
forum: Server Platforms
---

### Post by TheDigitalNinja on 2010-06-22
I'm trying to migrate our web farm (about 25 servers) from gentoo to ubuntu. When I try start the server I get the following error message.

```
Syntax error on line 10 of /etc/apache2/sites-enabled/00_default_vhost.conf:
Invalid command 'php_value', perhaps misspelled or defined by a module not included in the server configuration
```

I do NEED the php_value for the linuxodbc driver for as400. What module do I need to install to get this working?

Ubuntu Server 10.4 64bit

---

### Post by dapperdanny77 on 2010-06-22
please post the vhost section including this command

---

### Post by TheDigitalNinja on 2010-06-22
Here is the 00_default_vhost.conf

```
<VirtualHost *:80>

        #[]--------------------------------------[]
        #[] default vhost                        []
        #[]--------------------------------------[]
        ServerName farmdefault
        DocumentRoot /u01/www/production/tb
        #DocumentRoot /var/www/localhost/htdocs
        <Location ~ /.* >
                php_value include_path "/usr/share/php5:/u01/www/production/tb:/u01/www/production/mbs:/u01/www/settings/production"
                php_value odbc.default_db "DBNAME"
                php_value odbc.default_user "DBUSER"
                php_value odbc.default_pw "DBPASS"
        </Location>
        <Directory /*>
                Options +FollowSymLinks
                Order allow,deny
                Allow from all
        </Directory>
</VirtualHost>
```

---

### Post by cdenley on 2010-06-22
```

sudo apt-get install libapache2-mod-php5
sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```

---

### Post by dapperdanny77 on 2010-06-22
I'm quite sure there's no php_value directive for apache - so, this piece of code has to be put in the related php files. apache don't knows what to do with that.

---

### Post by TheDigitalNinja on 2010-06-22
I already have php installed. 

```
libapache2-mod-php5 is already the newest version.
```

I Figured I should post my other main config files.

Here is my apache2.conf, without the comments

```
ServerRoot "/etc/apache2"
LockFile /var/lock/apache2/accept.lock
PidFile ${APACHE_PID_FILE}
Timeout 300
KeepAlive On
MaxKeepAliveRequests 100
KeepAliveTimeout 15

<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    ServerLimit         375
    MaxClients          375
    MaxRequestsPerChild   0
</IfModule>

<IfModule mpm_worker_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

<IfModule mpm_event_module>
    StartServers          2
    MaxClients          150
    MinSpareThreads      25
    MaxSpareThreads      75
    ThreadLimit          64
    ThreadsPerChild      25
    MaxRequestsPerChild   0
</IfModule>

User apache
Group apache

AccessFileName .htaccess

<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>

DefaultType text/plain
HostnameLookups Off
ErrorLog /var/log/apache2/error.log
LogLevel warn
Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf
Include /etc/apache2/httpd.conf #this is where we load modules from
Include /etc/apache2/ports.conf
LogFormat "%v:%p %h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" vhost_combined
LogFormat "%h %l %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %O" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent
CustomLog /var/log/apache2/other_vhosts_access.log vhost_combined
Include /etc/apache2/conf.d/
Include /etc/apache2/vhosts.d/
```

And here is my http.conf where I load my modules (rather than mod-enabled/*.load files)

```
LoadModule actions_module /usr/lib/apache2/modules/mod_actions.so
LoadModule alias_module /usr/lib/apache2/modules/mod_alias.so
LoadModule asis_module /usr/lib/apache2/modules/mod_asis.so
LoadModule auth_basic_module /usr/lib/apache2/modules/mod_auth_basic.so
LoadModule authn_default_module /usr/lib/apache2/modules/mod_authn_default.so
LoadModule authn_file_module /usr/lib/apache2/modules/mod_authn_file.so
LoadModule authz_default_module /usr/lib/apache2/modules/mod_authz_default.so
LoadModule authz_groupfile_module /usr/lib/apache2/modules/mod_authz_groupfile.so
LoadModule authz_host_module /usr/lib/apache2/modules/mod_authz_host.so
LoadModule authz_user_module /usr/lib/apache2/modules/mod_authz_user.so
LoadModule autoindex_module /usr/lib/apache2/modules/mod_autoindex.so

<IfDefine CACHE>
LoadModule cache_module /usr/lib/apache2/modules/mod_cache.so
</IfDefine>
LoadModule cern_meta_module /usr/lib/apache2/modules/mod_cern_meta.so
LoadModule cgi_module /usr/lib/apache2/modules/mod_cgi.so
LoadModule charset_lite_module /usr/lib/apache2/modules/mod_charset_lite.so
<IfDefine DAV>
LoadModule dav_module /usr/lib/apache2/modules/mod_dav.so
</IfDefine>
<IfDefine DAV>
LoadModule dav_fs_module /usr/lib/apache2/modules/mod_dav_fs.so
</IfDefine>
LoadModule deflate_module /usr/lib/apache2/modules/mod_deflate.so
LoadModule dir_module /usr/lib/apache2/modules/mod_dir.so
<IfDefine CACHE>
LoadModule disk_cache_module /usr/lib/apache2/modules/mod_disk_cache.so
</IfDefine>
LoadModule env_module /usr/lib/apache2/modules/mod_env.so
LoadModule expires_module /usr/lib/apache2/modules/mod_expires.so
LoadModule ext_filter_module /usr/lib/apache2/modules/mod_ext_filter.so
<IfDefine CACHE>
LoadModule file_cache_module /usr/lib/apache2/modules/mod_file_cache.so
</IfDefine>
LoadModule filter_module /usr/lib/apache2/modules/mod_filter.so
LoadModule headers_module /usr/lib/apache2/modules/mod_headers.so
LoadModule include_module /usr/lib/apache2/modules/mod_include.so
<IfDefine INFO>
LoadModule info_module /usr/lib/apache2/modules/mod_info.so
</IfDefine>
LoadModule log_config_module /usr/lib/apache2/modules/mod_log_config.so
LoadModule logio_module /usr/lib/apache2/modules/mod_logio.so
<IfDefine CACHE>
LoadModule mem_cache_module /usr/lib/apache2/modules/mod_mem_cache.so
</IfDefine>
LoadModule mime_module /usr/lib/apache2/modules/mod_mime.so
LoadModule mime_magic_module /usr/lib/apache2/modules/mod_mime_magic.so
LoadModule negotiation_module /usr/lib/apache2/modules/mod_negotiation.so
LoadModule rewrite_module /usr/lib/apache2/modules/mod_rewrite.so
LoadModule setenvif_module /usr/lib/apache2/modules/mod_setenvif.so

<IfDefine SSL>
LoadModule ssl_module /usr/lib/apache2/modules/mod_ssl.so
</IfDefine>
<IfDefine STATUS>
LoadModule status_module /usr/lib/apache2/modules/mod_status.so
</IfDefine>
LoadModule unique_id_module /usr/lib/apache2/modules/mod_unique_id.so
<IfDefine USERDIR>
LoadModule userdir_module /usr/lib/apache2/modules/mod_userdir.so
</IfDefine>
LoadModule usertrack_module /usr/lib/apache2/modules/mod_usertrack.so

```

---

### Post by cdenley on 2010-06-22
> **dapperdanny77 said:**
> I'm quite sure there's no php_value directive for apache - so, this piece of code has to be put in the related php files. apache don't knows what to do with that.

[http://php.net/manual/en/configuration.changes.php](http://php.net/manual/en/configuration.changes.php)
> 
There are several Apache directives that allow you to change the PHP configuration from within the Apache configuration files.


---

### Post by cdenley on 2010-06-22
> **TheDigitalNinja said:**
> 
And here is my http.conf where I load my modules (rather than mod-enabled/*.load files)


Well, you have to load the php module. I already told you the correct way to do that in ubuntu. I wouldn't recommend using httpd.conf to load modules.

---

### Post by TheDigitalNinja on 2010-06-22
I should also add that all of these config files do work and are currently hosting a site that gets 100k hits a day. 

I'm just trying to move from Gentoo to Ubuntu.

---

### Post by dapperdanny77 on 2010-06-22
ahh - learned something new

---

### Post by cdenley on 2010-06-22
> **TheDigitalNinja said:**
> I should also add that all of these config files do work and are currently hosting a site that gets 100k hits a day. 

I'm just trying to move from Gentoo to Ubuntu.

I recommend not deviating from the ubuntu configuration for two reasons.

1. I believe installing modules will sometimes enable them using the ubuntu method. It would be confusing to have some modules enabled in httpd.conf, and some in the mods-enabled directory.

2. It becomes more difficult for other people to understand your configuration, whether you are seeking help on these forums, or someone else ends up working with your server for whatever reason.

---

### Post by TheDigitalNinja on 2010-06-22
I copied this from my 75_php.conf files in /mods-enabled and put it right into http.conf and it seemed to work.        

```
<IfModule !mod_php5.c>
                LoadModule php5_module    /usr/lib/apache2/modules/libphp5.so
        </IfModule>
```

Thanks

---

### Post by TheDigitalNinja on 2010-06-22
> **cdenley said:**
> I recommend not deviating from the ubuntu configuration for two reasons.

1. I believe installing modules will sometimes enable them using the ubuntu method. It would be confusing to have some modules enabled in httpd.conf, and some in the mods-enabled directory.

2. It becomes more difficult for other people to understand your configuration, whether you are seeking help on these forums, or someone else ends up working with your server for whatever reason.

Yeah, we hope to be able to get to the "ubuntu method" but as of right now the only way to get it to work is to be able to get half the sites ubuntu and half gentoo and slowly phaseout gentoo over the next month or so. But all the websites (as in conf files, passwd file, vhosts folders, and main drive) get pushed to the servers via scripts that the developers wrote every 15 mins. There is only one script, so there is only one way to do it. 

For instance I can modify http.conf but the developers cant, and they get to play around with vhosts.d/* but I cant.

---

