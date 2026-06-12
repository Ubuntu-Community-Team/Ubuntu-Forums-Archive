---
title: "Lamp &amp; fms"
date: 2010-02-28
forum: Server Platforms
---

### Post by andyd34 on 2010-02-28
I have installed ubuntu 9.10 server with LAMP and SAMBA I have also added FMS (Flash Media Server). LAMP and SAMBA are running fine but FMS doesn't have all its functionality, it cant stream rttp. 

I have read that their may be a port/ip conflict between apache and fms but was wondering if anyone else had the same issues as me. I have also installed FMS with apache2 on my XP laptop to get the httpd.conf file and see how its set up, here it is.

FMS / APACHE2 XP
```

#
# This is the main Apache server configuration file.  It contains the
# configuration directives that give the server its instructions.
# See <URL:http://httpd.apache.org/docs/2.2/> for detailed information.
# In particular, see
# <URL:http://httpd.apache.org/docs/2.2/mod/directives.html>
# for a discussion of each configuration directive.
#
# Please see httpd.conf.orig for the configuration of a default
# (non-FMS) installation of apache.

Listen 8134

AccessFileName .htaccess
ServerSignature On
UseCanonicalName Off
HostnameLookups Off

Timeout 120
KeepAlive On
MaxKeepAliveRequests 100
KeepAliveTimeout 15

ErrorLog logs/error_log
LogLevel info
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\"" combined
CustomLog logs/access_log combined

DocumentRoot "../webroot"

DirectoryIndex index.html index.html.var index.php index.php3 index.php4 index.php5 index.py index.pl index.rb 

<Directory />
    Options FollowSymLinks
    AllowOverride None
    Order allow,deny
    Allow from all
    Satisfy all
</Directory>

<Directory "../webroot">
    Options -Indexes FollowSymLinks
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>

Alias /documentation ../documentation/
<Directory ../documentation/>
    Options FollowSymLinks
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>


Alias /icons/ "icons/"
<Directory "icons">
    Options MultiViews FollowSymLinks
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>

Alias /error/ "error/"

ScriptAlias /cgi-bin/ "cgi-bin/"
<Directory "cgi-bin">
    AllowOverride None
    Options None
    Order allow,deny
    Allow from all
</Directory>
ScriptAlias /local-cgi-bin/ "local-cgi-bin/"
<Directory "local-cgi-bin">
    AllowOverride None
    Options None
    Order deny,allow
    Deny from all
    Allow from 127.0.0.1
</Directory>

<Location /server-status>
    SetHandler server-status
    Order deny,allow
    Deny from all
    Allow from 10.0.0.0/8
    Allow from 172.16.0.0/12
    Allow from 192.168.0.0/16
    Allow from 127.
</Location>
ExtendedStatus On
<Location /server-info>
    SetHandler server-info
    Order deny,allow
    Deny from all
    Allow from 10.0.0.0/8
    Allow from 172.16.0.0/12
    Allow from 192.168.0.0/16
    Allow from 127.
</Location>

<FilesMatch "^\.ht">
    Order allow,deny
    Deny from all
</FilesMatch>

<IfModule mpm_winnt_module>
    ThreadsPerChild 250
    MaxRequestsPerChild 0
</IfModule>
<IfModule worker_module>
    StartServers         2
    MaxClients         150
    MinSpareThreads     25
    MaxSpareThreads     75 
    ThreadsPerChild     25
    MaxRequestsPerChild  0
</IfModule>

LoadModule actions_module modules/mod_actions.so
LoadModule alias_module modules/mod_alias.so
LoadModule asis_module modules/mod_asis.so
LoadModule auth_basic_module modules/mod_auth_basic.so
LoadModule auth_digest_module modules/mod_auth_digest.so
LoadModule authn_anon_module modules/mod_authn_anon.so
#LoadModule authn_dbm_module modules/mod_authn_dbm.so
LoadModule authn_default_module modules/mod_authn_default.so
LoadModule authn_file_module modules/mod_authn_file.so
#LoadModule authz_dbm_module modules/mod_authz_dbm.so
LoadModule authz_default_module modules/mod_authz_default.so
LoadModule authz_groupfile_module modules/mod_authz_groupfile.so
LoadModule authz_host_module modules/mod_authz_host.so
LoadModule authz_user_module modules/mod_authz_user.so
LoadModule autoindex_module modules/mod_autoindex.so
#LoadModule cern_meta_module modules/mod_cern_meta.so
LoadModule cgi_module modules/mod_cgi.so
LoadModule dav_module modules/mod_dav.so
LoadModule dav_fs_module modules/mod_dav_fs.so
LoadModule deflate_module modules/mod_deflate.so
LoadModule dir_module modules/mod_dir.so
LoadModule env_module modules/mod_env.so
#LoadModule expires_module modules/mod_expires.so
#LoadModule file_cache_module modules/mod_file_cache.so
#LoadModule headers_module modules/mod_headers.so
LoadModule imagemap_module modules/mod_imagemap.so
LoadModule include_module modules/mod_include.so
LoadModule info_module modules/mod_info.so
LoadModule isapi_module modules/mod_isapi.so
LoadModule log_config_module modules/mod_log_config.so
LoadModule mime_module modules/mod_mime.so
LoadModule mime_magic_module modules/mod_mime_magic.so
#LoadModule proxy_module modules/mod_proxy.so
#LoadModule proxy_ajp_module modules/mod_proxy_ajp.so
#LoadModule proxy_balancer_module modules/mod_proxy_balancer.so
#LoadModule proxy_connect_module modules/mod_proxy_connect.so
#LoadModule proxy_http_module modules/mod_proxy_http.so
#LoadModule proxy_ftp_module modules/mod_proxy_ftp.so
LoadModule negotiation_module modules/mod_negotiation.so
LoadModule rewrite_module modules/mod_rewrite.so
LoadModule setenvif_module modules/mod_setenvif.so
#LoadModule speling_module modules/mod_speling.so
LoadModule status_module modules/mod_status.so
LoadModule unique_id_module modules/mod_unique_id.so
LoadModule userdir_module modules/mod_userdir.so
#LoadModule usertrack_module modules/mod_usertrack.so
#LoadModule vhost_alias_module modules/mod_vhost_alias.so
LoadModule ssl_module modules/mod_ssl.so

TypesConfig conf/mime.types
MIMEMagicFile conf/magic
DefaultType text/plain

AddType video/x-flv .flv

AddType application/x-compress .Z
AddType application/x-gzip .gz .tgz

AddHandler send-as-is asis
AddHandler type-map var
AddType text/html .shtml
AddOutputFilter INCLUDES .shtml

<IfModule ssl_module>
    SSLRandomSeed startup builtin
    SSLRandomSeed connect builtin
</IfModule>

<IfModule userdir_module>
    UserDir disable
</IfModule>

<IfModule dav_fs_module>
    DAVLockDB tmp/dav/lockdb
</IfModule>

IndexOptions FancyIndexing VersionSort NameWidth=* HTMLTable
AddIconByEncoding (CMP,/icons/compressed.gif) x-compress x-gzip
AddIconByType (TXT,/icons/text.gif) text/*
AddIconByType (IMG,/icons/image2.gif) image/*
AddIconByType (SND,/icons/sound2.gif) audio/*
AddIconByType (VID,/icons/movie.gif) video/*
AddIconByType (VID,/icons/movie.gif) application/x-shockwave-flash
AddIcon /icons/binary.gif .bin .exe
AddIcon /icons/binhex.gif .hqx
AddIcon /icons/tar.gif .tar
AddIcon /icons/world2.gif .wrl .wrl.gz .vrml .vrm .iv
AddIcon /icons/compressed.gif .Z .z .tgz .gz .zip
AddIcon /icons/a.gif .ps .ai .eps
AddIcon /icons/layout.gif .html .shtml .htm .pdf
AddIcon /icons/text.gif .txt
AddIcon /icons/c.gif .c
AddIcon /icons/p.gif .pl .py
AddIcon /icons/f.gif .for
AddIcon /icons/dvi.gif .dvi
AddIcon /icons/uuencoded.gif .uu
AddIcon /icons/script.gif .conf .sh .shar .csh .ksh .tcl
AddIcon /icons/tex.gif .tex
AddIcon /icons/bomb.gif core
AddIcon /icons/back.gif ..
AddIcon /icons/hand.right.gif README
AddIcon /icons/folder.gif ^^DIRECTORY^^
AddIcon /icons/blank.gif ^^BLANKICON^^
DefaultIcon /icons/unknown.gif
ReadmeName README.html
HeaderName HEADER.html
IndexIgnore .??* *~ *# HEADER* README* RCS CVS *,v *,t

AddLanguage ca .ca
AddLanguage cs .cz .cs
AddLanguage da .dk
AddLanguage de .de
AddLanguage el .el
AddLanguage en .en
AddLanguage eo .eo
AddLanguage es .es
AddLanguage et .et
AddLanguage fr .fr
AddLanguage he .he
AddLanguage hr .hr
AddLanguage it .it
AddLanguage ja .ja
AddLanguage ko .ko
AddLanguage ltz .ltz
AddLanguage nl .nl
AddLanguage nn .nn
AddLanguage no .no
AddLanguage pl .po
AddLanguage pt .pt
AddLanguage pt-BR .pt-br
AddLanguage ru .ru
AddLanguage sv .sv
AddLanguage zh-CN .zh-cn
AddLanguage zh-TW .zh-tw
LanguagePriority en ca cs da de el eo es et fr he hr it ja ko ltz nl nn no pl pt pt-BR ru sv zh-CN zh-TW
ForceLanguagePriority Prefer Fallback
AddDefaultCharset UTF-8

<IfModule mod_negotiation.c>
    <IfModule mod_include.c>
        <Directory "error">
            AllowOverride None
            Options IncludesNoExec
            AddOutputFilter Includes html
            AddHandler type-map var
            Order allow,deny
            Allow from all
            LanguagePriority en es de fr
            ForceLanguagePriority Prefer Fallback
        </Directory>
    </IfModule>
</IfModule>

BrowserMatch "Mozilla/2" nokeepalive
BrowserMatch "MSIE 4\.0b2;" nokeepalive downgrade-1.0 force-response-1.0
BrowserMatch "RealPlayer 4\.0" force-response-1.0
BrowserMatch "Java/1\.0" force-response-1.0
BrowserMatch "JDK/1\.0" force-response-1.0
BrowserMatch "Microsoft Data Access Internet Publishing Provider" redirect-carefully
BrowserMatch "MS FrontPage" redirect-carefully
BrowserMatch "^WebDrive" redirect-carefully
BrowserMatch "^WebDAVFS/1.[0123]" redirect-carefully
BrowserMatch "^gnome-vfs/1.0" redirect-carefully
BrowserMatch "^XML Spy" redirect-carefully
BrowserMatch "^Dreamweaver-WebDAV-SCM1" redirect-carefully

```

I have had a look at the httpd.conf in /etc/apache2/ on the ubuntu install and it's completely empty.

Can someone please help or give me some pointers to where I can get help because the howto's on this are a little vague.

Thanks

---

### Post by joberly on 2010-02-28
I'm not familiar with FMS, but if it uses its own built-in webserver, then there could be conflicts if both FMS + Apache are trying to run on port 80.

The Apache configurations for linux are located in /etc/apache2 and the main config file is apache2.conf, while the ports.conf is for the (obvious) port declarations!

EDIT: After a quick search, it seems documentation for Linux and FMS is .... non-existant! However this may be useful, as I don't know what configuration you chose to install, and I also do not know if the following pertains to just windows (I am assuming it was written as such)

From [http://help.adobe.com/en_US/FlashMediaServer/3.5_InstallingFMS/WS5b3ccc516d4fbf351e63e3d119ed5bf6c6-7ff6.html]("http://help.adobe.com/en_US/FlashMediaServer/3.5_InstallingFMS/WS5b3ccc516d4fbf351e63e3d119ed5bf6c6-7ff6.html")

You can choose to install Apache HTTP Server with Flash Media Server. If you install and enable Apache, Flash Media Server can act as a progressive download server and as a streaming server. You can write client-side ActionScript that serves video over HTTP if a client cannot use RTMP. You can also serve client SWF files, HTML files, and other page-related files such as CSS, Javascript, AIR applications, and images over HTTP.

During installation of Flash Media Server, the default option is to install Apache. If you want to use your own web server, do not install Apache. You can proxy HTTP connections from your own web server through Flash Media Server.

---

### Post by andyd34 on 2010-02-28
Thnaks for the reply, I chose not to install apache from within the fms install as it has already been installed with LAMP.

As you have noticed from your google, instructions are few and far between but i'll carry on playing with it and try different configurations

---

### Post by andyd34 on 2010-02-28
I now think I am getting some where. When I reboot the machine apache2 will not start, port 80 is already in use then gives a message cannot bind to port already served by 0.0.0.0:80

if i stop fms
> /etc/init.d/fms stop

then start apache2
> /etc/init.d/apache2 start

then restart fms
> /etc/init.d/fms start

everything works fine. Is their a way to change the order in which programs boot in ubuntu so I can make sure apache2 starts before fms

---

