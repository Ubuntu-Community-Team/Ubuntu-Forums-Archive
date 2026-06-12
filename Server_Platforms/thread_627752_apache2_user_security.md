---
title: "apache2 user security?"
date: 2007-11-30
forum: Server Platforms
---

### Post by downat420 on 2007-11-30
Server Specs:
Ubuntu 7.10
Apache2
php5
mysql

I use an open source social networking site called dolphin from boonex.com. I am hosting it myself until it is developed. Here is the problem:

When a user joins my site (so far only test users) the user information is saved in the mysql database but the profile is not created. For instance the site is located in:
/var/www/sitename/community

when i attempt to view a user profile via the web i get a 404 error and this is the link.
[www.sitename.com/community/profile](www.sitename.com/community/profile)

the problem is the profile folder is not being created in:
/var/www/sitename/community

Here is my config file:

user www-data
group www-data

NameVirtualHost *:80
<VirtualHost *:80>
ServerAdmin webmaster@localhost
ServerName [www.sitename.com](www.sitename.com)
ServerAlias *.sitename.com
DocumentRoot /var/www/sitename
ErrorLog /var/www/sitename/error_log
<Directory /var/www/sitename/>
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /var/www/sitename/>
Options Indexes FollowSymLinks MultiViews
AllowOverride All
Order allow,deny
allow from all
</Directory>

yatta yatta

end of config file.

Thanks in advance,
zach

---

### Post by crouton on 2007-11-30
Check the appropriate log in /var/log and see what error you're getting.  Also, do you have the correct permissions for the /community directory?

---

### Post by downat420 on 2007-11-30
in /var/log/apache2/error.log i get a lot of these

[Mon Nov 26 22:14:38 2007] [error] [client 24.11.23.214] File does not exist: /var/www/sitename/community/profile, referer: [http://sitename.com/community/browse.php](http://sitename.com/community/browse.php)

I know that the file does not exist because it is not being created.  My problem is setting up the site to create that file.  My guess is the permissions are not right for the community directory.

---

### Post by crouton on 2007-12-03
Check permissions for /sitename as well as /community.

---

### Post by downat420 on 2007-12-04
Thanks for your help so far crouton.
To be honest I am not sure how to do that or what they should be.

---

### Post by downat420 on 2007-12-13
I am still looking for help on this one.  I do not know what the set the directory permission to.

---

