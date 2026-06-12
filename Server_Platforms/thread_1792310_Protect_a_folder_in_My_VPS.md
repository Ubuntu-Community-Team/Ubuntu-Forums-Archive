---
title: "Protect a folder in My VPS"
date: 2011-06-28
forum: Server Platforms
---

### Post by ibrahim.k on 2011-06-28
Hi, I want to protect one of the folders in my VPS which is running under Ubuntu server 10.04 LTS I've tried doing this using .htaccess and I am being prompted for a user name and  a password but when i enter the user name and the password I get the same window again but I am sure that I am entering the correct information. this is the .htaccess file 

AuthUserFile /var/www/folder/.htpasswd 
AuthName "Authorization Required" 
AuthType Basic 
require user

 this file is located in the same folder that I want to protect.

and this is the .htpasswd 
user:MgmeYBwL7D1E 
 In the same folder that I want to protect

Many thanks.

---

### Post by falko on 2011-06-28
Any errors in Apache's error log?

Also check the permissions of your .htpasswd file - it mustb e readable by the Apache user.

---

