---
title: "Help configuring apache1.3 + modperl"
date: 2005-08-26
forum: Server Platforms
---

### Post by sapo on 2005-08-26
It is drivin me nuts.. i was trying some config and it worked once.. but now it isnt working anymore.. help please... here my configs:

httpd.conf
```
##
## httpd.conf -- Apache HTTP server configuration file
##



ServerType standalone


ServerRoot /etc/apache


LockFile /var/lock/apache.lock


PidFile /var/run/apache.pid


ScoreBoardFile /var/run/apache.scoreboard



Timeout 300

KeepAlive On

MaxKeepAliveRequests 100


KeepAliveTimeout 15


MinSpareServers 5
MaxSpareServers 10


StartServers 5


MaxClients 150


MaxRequestsPerChild 100





Include /etc/apache/modules.conf


<IfModule mod_status.c>
  ExtendedStatus On
</IfModule>




Port 1000


User www-data
Group www-data


ServerAdmin asudh@aushu

ServerName xgn.no-ip.org

DocumentRoot /home/sapo/public_html


<Directory />
    Options SymLinksIfOwnerMatch
    AllowOverride None
</Directory>




<Directory /home/sapo/public_html>


    Options Indexes Includes FollowSymLinks MultiViews


    AllowOverride None


    Order allow,deny
    Allow from all
</Directory>


<IfModule mod_userdir.c>
    UserDir public_html

    <Directory /home/*/public_html>
        AllowOverride FileInfo AuthConfig Limit
        Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
        <Limit GET POST OPTIONS PROPFIND>
            Order allow,deny
            Allow from all
        </Limit>
        <Limit PUT DELETE PATCH PROPPATCH MKCOL COPY MOVE LOCK UNLOCK>
            Order deny,allow
            Deny from all
        </Limit>
    </Directory>
</IfModule>


<IfModule mod_dir.c>
    DirectoryIndex index.html index.htm index.shtml index.cgi index.php
</IfModule>

AccessFileName .htaccess


<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
</Files>


UseCanonicalName Off

TypesConfig /etc/mime.types


DefaultType text/plain


<IfModule mod_mime_magic.c>
    MIMEMagicFile /usr/share/misc/file/magic.mime
</IfModule>


HostnameLookups Off


ErrorLog /var/log/apache/error.log

LogLevel warn


LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" \"%{forensic-id}n\" %T %v" full
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" \"%{forensic-id}n\" %P %T" debug
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{Referer}i\" \"%{User-Agent}i\" \"%{forensic-id}n\"" combined
LogFormat "%h %l %u %t \"%r\" %>s %b \"%{forensic-id}n\"" forensic
LogFormat "%h %l %u %t \"%r\" %>s %b" common
LogFormat "%{Referer}i -> %U" referer
LogFormat "%{User-agent}i" agent




CustomLog /var/log/apache/access.log combined

<IfModule mod_log_forensic.c>
 ForensicLog /var/log/apache/forensic.log
</IfModule>


<IfModule mod_backtrace.c>
 EnableExceptionHook On

</IfModule>

<IfModule mod_whatkilledus.c>
 EnableExceptionHook On

</IfModule>


ServerSignature On




<IfModule mod_alias.c>
    Alias /icons/ /usr/share/apache/icons/

    <Directory /usr/share/apache/icons>
         Options Indexes MultiViews
         AllowOverride None
         Order allow,deny
         Allow from all
    </Directory>

    Alias /images/ /usr/share/images/

    <Directory /usr/share/images>
         Options MultiViews
         AllowOverride None
         Order allow,deny
         Allow from all
    </Directory>
</IfModule>


<IfModule mod_alias.c>
    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/


    <Directory /usr/lib/cgi-bin/>
        AllowOverride None
        Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>
</IfModule>




<IfModule mod_autoindex.c>


    IndexOptions FancyIndexing NameWidth=*


    AddIconByEncoding (CMP,/icons/compressed.gif) x-compress x-gzip

    AddIconByType (TXT,/icons/text.gif) text/*
    AddIconByType (IMG,/icons/image2.gif) image/*
    AddIconByType (SND,/icons/sound2.gif) audio/*
    AddIconByType (VID,/icons/movie.gif) video/*

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
    AddIcon /icons/deb.gif .deb

    AddIcon /icons/back.gif ..
    AddIcon /icons/hand.right.gif README
    AddIcon /icons/folder.gif ^^DIRECTORY^^
    AddIcon /icons/blank.gif ^^BLANKICON^^


    DefaultIcon /icons/unknown.gif



    ReadmeName README.html
    HeaderName HEADER.html

    IndexIgnore .??* *~ *# HEADER.html HEADER.txt RCS CVS *,v *,t


</IfModule>

<IfModule mod_mime.c>



    AddEncoding x-compress Z
    AddEncoding x-gzip gz tgz

 
    AddLanguage da .dk
    AddLanguage nl .nl
    AddLanguage en .en
    AddLanguage et .ee
    AddLanguage fr .fr
    AddLanguage de .de
    AddLanguage el .el
    AddLanguage it .it
    AddLanguage ja .ja
    AddCharset ISO-2022-JP .jis
    AddLanguage pl .po
    AddCharset ISO-8859-2 .iso-pl
    AddLanguage pt .pt
    AddLanguage pt-br .pt-br
    AddLanguage lb .lu
    AddLanguage ca .ca
    AddLanguage es .es
    AddLanguage sv .se
    AddLanguage cs .cz


    <IfModule mod_negotiation.c>
        LanguagePriority en da nl et fr de el it ja pl pt pt-br lb ca es sv
    </IfModule>


    AddType application/x-httpd-php .php
    AddType application/x-httpd-php-source .phps

    AddType application/x-tar .tgz
    AddType image/bmp .bmp

    # hdml
    AddType text/x-hdml .hdml


    AddHandler cgi-script .cgi .sh .pl

    <IfModule mod_include.c>
     AddType text/html .shtml
     AddHandler server-parsed .shtml
    </IfModule>





</IfModule>


AddDefaultCharset on



<IfModule mod_setenvif.c>

    BrowserMatch "Mozilla/2" nokeepalive
    BrowserMatch "MSIE 4\.0b2;" nokeepalive downgrade-1.0 force-response-1.0

    BrowserMatch "RealPlayer 4\.0" force-response-1.0
    BrowserMatch "Java/1\.0" force-response-1.0
    BrowserMatch "JDK/1\.0" force-response-1.0
</IfModule>


[b]# If the perl module is installed, this will be enabled.
<IfModule mod_perl.c>
  <IfModule mod_alias.c>
   Alias /perl /home/*/public_html/perl
  </IfModule>
  <Location /perl>
    SetHandler perl-script
    PerlHandler Apache::Registry
    Options +ExecCGI
    Order allow,deny
    Allow from all
  </Location>
</IfModule>
[/b]



<Location /server-status>
    SetHandler server-status
    Order deny,allow
    Allow from all
</Location>


<Location /server-info>
    SetHandler server-info
    Order deny,allow
    Allow from all
</Location>


<IfModule mod_alias.c>
 Alias /doc/ /usr/share/doc/
</IfModule>

<Location /doc>
  order deny,allow
  deny from all
  allow from 127.0.0.0/255.0.0.0
  Options Indexes FollowSymLinks MultiViews
</Location>


Include /etc/apache/conf.d

```

i m getting FORBIDDEN but sometimes it tries to download the file
[http://xgn.no-ip.org:1000/~sapo/perl/perltest.pl](http://xgn.no-ip.org:1000/~sapo/perl/perltest.pl)

I ll leave the server as it is.. if you wanna see the server info access:

[http://xgn.no-ip.org:1000/server-info](http://xgn.no-ip.org:1000/server-info)

Thanx for any help :)

---

### Post by amohanty on 2005-08-27
what does this return:

ls -l /home/<a valid username>/public_html/perl

If the last three dont look like r-x or at least --x you are in trouble.


HTH
AM

---

### Post by sapo on 2005-08-27
[QUOTE=amohanty]what does this return:

ls -l /home/<a valid username>/public_html/perl

If the last three dont look like r-x or at least --x you are in trouble.


HTH
AM[/QUOTE]

```

sapo@ubuntu:~$ ls -l /home/sapo/public_html/perl/
-rwxr-xr-x  1 sapo sapo    144 2004-04-19 17:44 perltest1.pl
-rwxr-xr-x  1 sapo sapo     81 2004-04-23 00:06 perltest.pl

```

---

### Post by amohanty on 2005-08-27
Can you post the tail of your logs?

Thanks.
AM

---

### Post by sapo on 2005-08-27
[QUOTE=amohanty]Can you post the tail of your logs?

Thanks.
AM[/QUOTE]

Here the error:

```
[Fri Aug 26 05:23:04 2005] [error] [client 66.159.229.150] Options ExecCGI is off in this directory: /home/sapo/public_html/perl/perltest.pl
```

thanx for helping  :grin:

---

### Post by sapo on 2005-08-28
Please somebody help.. i need to put it to work  ](*,)

---

### Post by amohanty on 2005-08-28
Just as a test try puttin the mod_perl directives outside of the <IfModule...> block. IT of course assumes that mod_perl.c is available, but I would like to see f it works at all.

AM

---

### Post by sapo on 2005-08-29
[QUOTE=amohanty]Just as a test try puttin the mod_perl directives outside of the <IfModule...> block. IT of course assumes that mod_perl.c is available, but I would like to see f it works at all.

AM[/QUOTE]
 I tried it.. but no luck...

i ve changed some stuff and now the browser tries to download the file instead of executing :(

---

### Post by amohanty on 2005-08-30
I am still getting a 500. Try the mozilla live-http-header and see what mime type is returned by the server int he response.

AM

---

