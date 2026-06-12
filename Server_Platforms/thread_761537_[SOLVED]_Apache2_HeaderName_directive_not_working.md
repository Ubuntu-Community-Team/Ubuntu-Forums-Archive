---
title: "[SOLVED] Apache2 HeaderName directive not working"
date: 2008-04-21
forum: Server Platforms
---

### Post by jazzgossen on 2008-04-21
I'm trying to use the neat-looking [indices package]("http://antisleep.com/software/indices/"), but I'm having trouble. I added the following code to my /etc/apache2/apache2.conf. The icons get changed as they should, and ReadmeName works too, but the HeaderName directive seems to have no effect. The file /indices/header.php does not get included when I browse to the directory http://myhost/img/

Any ideas why? The file is readable by everybody.

```
<Directory /var/www/img/>
   Options +Indexes

   IndexOptions FancyIndexing
   IndexOptions FoldersFirst IgnoreCase XHTML NameWidth=*
   IndexOptions SuppressHTMLPreamble SuppressRules HTMLTable
   IndexOptions IconHeight=16 IconWidth=16
   IndexOptions SuppressDescription

   IndexIgnore readme.html

   HeaderName /indices/header.php
   ReadmeName /indices/footer.html

   DefaultIcon /indices/icons/text.png

   AddIcon /indices/icons/blank.gif        ^^BLANKICON^^
   AddIcon /indices/icons/dir.png          ^^DIRECTORY^^

   AddIcon /indices/icons/back.png         ..
   AddIcon /indices/icons/comp.png         .comp
   AddIcon /indices/icons/compressed.png   .zip .tar .tgz
   AddIcon /indices/icons/doc.png          .doc
   AddIcon /indices/icons/image.png        .jpg .png .gif .tif .tiff
   AddIcon /indices/icons/java.png         .java
   AddIcon /indices/icons/js.png           .js
   AddIcon /indices/icons/movie-ms.gif     .wmv .avi
   AddIcon /indices/icons/mov.png          .mov .qt
   AddIcon /indices/icons/pdf.png          .pdf
   AddIcon /indices/icons/php.png          .php
   AddIcon /indices/icons/ppt.png          .ppt
   AddIcon /indices/icons/ps.png           .ps
   AddIcon /indices/icons/sound.png        .mp3 .wav .m4a
   AddIcon /indices/icons/text.png         .text .html .htm
   AddIcon /indices/icons/xls.png          .xls
</Directory>

```

---

### Post by MJN on 2008-04-21
Check the manual:

[http://httpd.apache.org/docs/2.0/mod/mod_autoindex.html#headername](http://httpd.apache.org/docs/2.0/mod/mod_autoindex.html#headername)

Your PHP files (dictated by the .php extension) are not treated as type text/ but rather application/x-httpd-php

It might be possible to work around this but I don't know how. Perhaps embedding your PHP code inside a standard HTML document would work.

Mathew

---

### Post by gscottevans on 2008-04-21
Hi there, I wrote Indices.

Indices includes a second bit of .htaccess hackery that tells Apache to parse your header file as PHP.  If you're using .htaccess files, it needs to go in the same place as the header file itself; I assume you could do an apache2.conf directive that points at <Directory /var/www/indices> or whatever is right for you.

```

# In order for the PHP file to execute in a header, need to have a major type of text
AddType text/html .php
AddHandler application/x-httpd-php .php
Options -Indexes
```

---

### Post by jazzgossen on 2008-04-21
Thanks, that's it.

---

### Post by RHF on 2008-06-07
Hi there,

I hope I'm not trolling by coming back to this, but I don't think it warrants opening a new post about this issue, I've been getting stuck on this for the last few hours and it's really beginning to fray my nerves.

I want to be able to provide pretty looking folder listings for one of my servers.

But, whatever I do, the readme/headers are ignored.

This is my .htaccess file (inside the root /var/www folder, as well as the folder I want to look pretty)

```
AddType text/html .php
AddHandler application/x-httpd-php .php
Options -Indexes
IndexOptions FancyIndexing FoldersFirst SuppressLastModified IconsAreLinks NameWidth=* IconWidth=32 IconHeight=32
HeaderName header.php
ReadmeName readme.php

<IfModule mod_autoindex.c>
IndexOptions FancyIndexing FoldersFirst SuppressLastModified IconsAreLinks NameWidth=* IconWidth=32 IconHeight=32
HeaderName header.php
ReadmeName readme.php
</IfModule>

```

Here is my **/etc/apache2/sites-enabled/000-default** file:

```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>

<Directory /var/www/sandbox/>
   Options +Indexes

   IndexOptions FancyIndexing
   IndexOptions FoldersFirst IgnoreCase XHTML NameWidth=*
   IndexOptions SuppressHTMLPreamble SuppressRules HTMLTable
   IndexOptions IconHeight=16 IconWidth=16
   IndexOptions SuppressDescription

   IndexIgnore readme.html

   HeaderName header.php
   ReadmeName readme.php

</Directory>

        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
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
        ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
   </Directory>

</VirtualHost>
```

I can't for the life of me sus out why it wont just work. Please,  if anyone can throw me a bone, I'd be very glad. :)

---

### Post by RHF on 2008-06-07
**Just an update**

[edit]

Worked it out, I set the allowoverride to all, and that fixed it :)

       ```
 <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride **None**
                Order allow,deny
                allow from all
        </Directory>
```



[/edit]

I've downloaded Scott Evan's indices modification, removed all of my previous tampering, and installed it.

It still doesn't seem to be working. This really has me stumped.

[http://gammasite.dontassrape.us/sandbox/](http://gammasite.dontassrape.us/sandbox/) - is the folder I would like to make pretty.

---

