---
title: "Where do I put .htaccess to protect awstats"
date: 2009-07-29
forum: Server Platforms
---

### Post by MechaMechanism on 2009-07-29
SOLVED

EDIT
I ended up doing the below which is prefered apparently over .htaccess so says Apache docs.
```
<Directory /usr/lib/cgi-bin>
<Files awstats.pl>
Order Deny,Allow
Deny from all
Allow from 127.0.0.0/255.0.0.0 ::1/128
</Files>
</Directory>

<Location /awstats>
DirectoryIndex awstats.pl
</Location>
```I'm trying to protect awstats with .htaccess.  For the life of me I can't seem to figure out where to put the .htaccess file.  I have these possible locations:

/usr/share/awstats
/usr/lib/cgi-bin
/etc/awstats
/etc/apache2/conf.d

For awstats I followed the tutorial here at [http://ubuntu-tutorials.com/2008/01/16/configuring-awstats-on-ubuntu-server/](http://ubuntu-tutorials.com/2008/01/16/configuring-awstats-on-ubuntu-server/)

And for .htaccess I followed the tutorial here at [http://ubuntu-tutorials.com/2007/10/06/limiting-access-to-websitesdirectories-with-htaccess/](http://ubuntu-tutorials.com/2007/10/06/limiting-access-to-websitesdirectories-with-htaccess/)

My .htaccess file
```
require user CENSORED
AuthType basic
AuthName "CENSORED!"
AuthUserFile /path/to/.htpasswd
```My .htpasswd is an dir owned by root but the file is www-data.

---

