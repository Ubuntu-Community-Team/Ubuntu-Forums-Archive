---
title: "apache basic auth for subdirectories"
date: 2008-07-24
forum: Server Platforms
---

### Post by [pl]ice on 2008-07-24
Hi,
 i would like to protect the directory /var/www/ftp/ with password, so i created the config below. It works,asks for user etc. BUT i cannot see any of the subfolders, its not visible or if i type manualy the addres, i got access denied. Is there other way, or i have to put .htaccess in all subfolders for this to work :(


<Directory "/var/www/ftp/">
  AllowOverride AuthConfig
  AuthType Basic
  AuthName "Protected Site test"
  AuthUserFile /etc/server/htpasswd
  Require valid-user
  Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
  Order allow,deny
  Allow from all
</Directory>

Could someone pls give me example? i'm starting to read apache book now, to learn :)

big thanks!
EDIT:
new config... ( better go and read more)!!!

<Directory /var/www/>
   Options +FollowSymLinks
   AllowOverride None
   Order allow,deny
   Allow from all
</Directory>




<Directory "/var/www/ftp/">
Options +SymLinksIfOwnerMatch 
  AllowOverride None
  AuthType Basic
  AuthName "Prtected Site test"
  AuthUserFile /etc/server/htpasswd
  Require valid-user

---

### Post by Bachstelze on 2008-07-25
Most likely, Apache doesn't have permission to access those subfolders.

---

### Post by [pl]ice on 2008-07-25
> **HymnToLife said:**
> Most likely, Apache doesn't have permission to access those subfolders.
in what way?
i found that writing directory /var/www , then setting up /var/www/ftp password protected worked. yet, the directory /var/www/ftp by itself did not work, even when i had all the settings. Its puzzling.
thanks

---

