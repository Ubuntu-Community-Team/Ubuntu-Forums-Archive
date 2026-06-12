---
title: "Apache2/Webdav problems on windows client"
date: 2006-01-18
forum: Server Platforms
---

### Post by wthing on 2006-01-18
Hi all

I have a problem with my webdav (Apache2/ubuntu 5.10) server, where I open the dav-enabled folder in internet explorer (win2000, XP) and recieve an error along the lines of "Internet explorer cannot open the site [] as a web folder.  Would you like to view in standard view?".  Works fine with konqueror/nautilus.  Any ideas???  Relevant snips of config are below:

===apache.conf===
BrowserMatch "Microsoft Data Access Internet Publishing Provider" redirect-carefully
BrowserMatch "Microsoft Data Access Internet Publishing Provider DAV 1.1" redirect-carefully
BrowserMatch "Microsoft-WebDAV-MiniRedir/5.1.2600" redirect-carefully
BrowserMatch "Mozilla/2.0 (compatible; MS FrontPage 4.0)" redirect-carefully
BrowserMatch "MSFrontPage/4.0" redirect-carefully
BrowserMatch "^WebDrive" redirect-carefully
BrowserMatch "^gnome-vfs" redirect-carefully
BrowserMatch "^WebDAVFS/1.[012]" redirect-carefully

===modules-enabled/webdav.load===
LoadModule dav_module /usr/lib/apache2/modules/mod_dav.so
LoadModule dav_fs_module /usr/lib/apache2/modules/mod_dav_fs.so

===modules-enabled/webdav.conf===
DAVLockDB /var/lock/apache2/DAVLock

===sites-enabled/000-default.conf===
<Directory /var/www/dav>
                Dav on
                AllowOverride None
                Options Indexes
                AuthName "webdav-curlyone"
                AuthType Digest
                AuthDigestFile /etc/apache2/dav-users
                Require valid-user
</Directory>

======
Thanks heaps :)   Wthing

---

### Post by anglerud on 2006-08-25
Gah, I have the exact same problem - if anyone's found a solution to this, I'd love to hear it as well.

---

### Post by anglerud on 2006-08-26
Ok, this post helped me: [http://ubuntuforums.org/showthread.php?t=141263](http://ubuntuforums.org/showthread.php?t=141263)

---

