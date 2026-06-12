---
title: "Problem setting up .htaccess in apache2"
date: 2009-01-28
forum: Server Platforms
---

### Post by tstack77 on 2009-01-28
I am trying to password protect a sub-directory on my server using .htaccess. I have created my .htpasswd file for user stack in /etc/apache2:

~$ htpasswd -c /etc/apache2/.htpasswd stack
New password: *****
Re-type new password: *****
Adding password for user stack

Created an .htaccess file in the directory /var/www/photos/.htaccess:

AuthUserFile  /etc/apache2/.htpasswd
AuthGroupFile /dev/null
AuthName  Hello internets! **<---------SOLVED! Needed quotes on "Hello internets!"**
AuthType Basic
require valid-user

And modified my site in /etc/apache2/sites-available/default (changes in **Bold**):

DocumentRoot /var/www/
<Directory />
	Options FollowSymLinks
	AllowOverride None
</Directory>
<Directory /var/www/**photos/**>
	Options Indexes FollowSymLinks MultiViews
	AllowOverride **AuthConfig**
	Order allow,deny
	**require valid-user**
</Directory>

After restarting apache and trying to go to my photos directory, I get an Internal Server Error. If I change the 'AllowOverride' section above back to none, I can access the directory but without the password protection.

I know I'm close but can't figure out where I went wrong...ideas?

---

