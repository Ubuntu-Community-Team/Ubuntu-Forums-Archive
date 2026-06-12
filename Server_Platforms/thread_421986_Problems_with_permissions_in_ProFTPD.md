---
title: "Problems with permissions in ProFTPD"
date: 2007-04-24
forum: Server Platforms
---

### Post by Torahteen on 2007-04-24
Hey guys... I'm not sure if this has been asked before, so sorry if I'm being newbish :(. I followed the tutorial here: [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)

This is an FTP server to compliment my Apache web server, so I've got a user called webadmin that has the home directory of /var/www/, I can get into the server fine using KFTPGrabber, But when I try to delete any files, I get permission denied. I thought I had the right permissions allowed, but maybe not... here's the permissions part:

<Directory /var/www/>
Umask 022 022
AllowOverwrite on
<LIMIT RMD DELE READ WRITE STOR CWD MKD>
AllowAll
</Limit>
</Directory>

Did I type something wrong? Or what? Thanks in advance for the help.

Sorry if this is the wrong place to ask, but I couldn't get help elsewhere :P

---

### Post by strixy on 2007-04-25
> when I try to delete any files, I get permission denied.


I'm no pro with this (ha!) but this DELE looks suspect...

<LIMIT RMD **DELE** READ WRITE STOR CWD MKD>

Try removing that. Also check the file permissions (ls -l )

Also check if the file group is set to webadmin group.

or snag everything with 

sudo chgrp -R webadmin /var/www
sudo chmod -R 774 /var/www

Apache runs under www-admin, so they should be chowned to that and grouped to webadmin. Chmoded to 774 (rwx-rwx-r..) or 754 is groovy too.

---

