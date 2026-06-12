---
title: "phpmyadmin - users and logging in"
date: 2007-08-22
forum: Server Platforms
---

### Post by Roo-Kun on 2007-08-22
Hey,

Just tried installing phpmyadmin this morning via synaptic. Installed but it didn't let me log in so I removed it. I then downloaded the files from the phpmyadmin website. Worked.

I was farting about and looking at what was what and I removed the root users be accident. Didn't realise I clicked for them to be DELETED. I tried using what was suggested and adding a user though the "/script/setup.php" file. 

Anyway, I've removed it by deleting the phpmyamin folder and tried putting a new version on and no matter how many times I do it I always get "#1045 - Access denied for user 'root'@'localhost' (using password: NO) "

Can anyone help me out? Add the user back or something.

Many thanks.

---

### Post by iskatyel on 2007-08-28
You may have sorted this already, but phpmyadmin is going straight to the mysql database for authentication so if you deleted the root user, you need to set up a new root user for mysql.  I have never tried to put a new root user in but, to create one in the first place you would enter:
```
#mysqladmin -u root password new_password
```
Hope that helps.
Dan

---

### Post by Roo-Kun on 2007-08-28
Got it working now, thanks.  =D Just need to password protect phpmyadmin now.  =/

---

### Post by iskatyel on 2007-08-28
On password protecting phpmyadmin - using an .htaccess file within the directory is MUCH less efficient than putting the instruction into the site config.  Try something like this:
```
<Directory /var/www/phpmyadmin>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/8 your.ip.add.ress/32
        <IfModule mod_authn_file.c>
                AuthType Basic
                AuthName "Authorized Users Only"
                AuthUserFile /var/.htpasswd
        </IfModule>
        Require valid-user
</Directory>
```
Create the /var/.htpasswd file like this (you can put it anywhere, but DON'T put it in a web-visible location
```
#htpasswd -c /var/.htpasswd username password
```

---

