---
title: "Warning: symlink(): Operation not permitted"
date: 2005-07-28
forum: Server Platforms
---

### Post by higgins on 2005-07-28
Hello

I am running Gallery on Ubuntu with Apache PHP and Mysql. However I keep getting the following errors with my scripts:

Warning: symlink(): Operation not permitted
Warning: chmod(): Operation not permitted

I do not have safe mode on (PHP). Is there anything else that would explain why I am getting these errors? I have mapped the Gallery URL to a folder outside /var/www/. The exact details of  /etc/apache2/conf.d/alias is listed below:

[PHP]
Alias /gallery2 /home/tim/G/gallery2
<Directory "/home/tim/G/gallery2">
	Options Indexes FollowSymLinks
  	AllowOverride All
  	Order allow,deny
  	Allow from all
</Directory>[/PHP]

Any help with this would be great.


[B]
System Information[/B]
Gallery version 	2.0-beta-4
PHP version 	4.3.10-10ubuntu4 apache2handler
Webserver 	Apache/2.0.53 (Ubuntu) PHP/4.3.10-10ubuntu4
Database 	mysql 4.0.23_Debian-3ubuntu2-log
Toolkits 	ImageMagick, NetPBM
Operating system 	Linux ubuntu 2.6.10-5-k7 #1 Fri Jun 24 18:51:20 UTC 2005 i686
Browser 	Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.7.10) Gecko/20050721 Firefox/1.0.4 (Ubuntu package 1.0.6)

---

### Post by heimo on 2005-07-28
I'd be wathing for owners and permissions of files and directories - maybe something needs to be in www-data group. That's what's my first hunch.

---

### Post by higgins on 2005-07-28
heimo, could you expand on this a little bit. I'm new to Linux, but learning. What group should i add www-data to?

---

### Post by heimo on 2005-07-28
[color=#000000][color=#dd0000][color=black]
I'd check that files and directories belong to www-data (which is user that Apache runs with by default). Both www-data user and www-data group exist. I'd add myself to group www-data and change files and directories in /home/tim/G/gallery2 to be owned by www-data:www-data (user:group). Sorry if I'm being complex. I try to clarify and give example..

chmod command changes file/directory permissions (you can also use graphical tools to do this), chown changes ownerships (both user and group) of files/dirs and with chgrp you can change just group ownership. www-data user belongs to www-data group, your username probably belongs to group which has same name as your username

I'm not using too much time to think this, so I may make mistakes.
[/color][/color][/color][color=#000000][color=#dd0000][color=black]
[/color][/color][/color] ```
chgrp www-data /home/tim/G/gallery2
[changes that one dir to group www-data]

chown -R www-data:www-data /home/tim/G/gallery2/*
[changes ownership to user www-data, group www-data in all files under that dir]

chgrp -R www-data /home/tim/G/gallery2/*
[changes almost everything under that dir to www-data group]

chmod g+rw [somefile_or_dirname_here]
[gives read and write permissions for the group which owns the file/dir]
[color=#000000][color=#dd0000][color=black]
[/color][/color][/color] chmod u+rw [somefile_or_dirname_here]
 [gives read and write permissions for the user which owns the file/dir][color=#000000][color=#dd0000][color=black]
[/color][/color][/color]
```
*) for more, see *man chmod / man chown / man chgrp *or ask

What I was thinking is that the gallery software is trying to make a symlink and chmod on some files/dirs under that dir ([color=#000000][color=#dd0000][color=black]/home/tim/G/gallery2), but the www-data doesn't have permission to do that. To be able to change file/dir permissions, you need to own that file/dir (being in the group that owns the file/dir is not enough). So probably www-data needs to own something under that directory, and to be able to make symlinks, it needs write permission to the directory it tries to use (to place the symlink).

Hmm.. Hopefully I didn't confuse more than help.

My initial guess of this problem may also be off. But file permissions is definitely what I'd go looking first.
[/color][/color][/color]

---

