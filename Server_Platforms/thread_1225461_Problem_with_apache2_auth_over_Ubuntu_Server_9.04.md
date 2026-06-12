---
title: "Problem with apache2 auth over Ubuntu Server 9.04"
date: 2009-07-28
forum: Server Platforms
---

### Post by Gashnark on 2009-07-28
Hi there, I need help related with apache2 mod_access or apache2 mod_auth.
I have installed ubuntu Server 9.04 x64, and I'm trying to configure the authentication by user of apache, but when I open the folder with my .htaccess I can see the folder contents without password authentication.
In the "/etc/apache2/apache2.conf" file I have:
```
<Directory /var/www/>
AllowOverride AuthConfig
</Directory>

```I don't know if there's a step I'm missing, maybe I need to enable mod_access but it isn't listed in "$ a2enmod", so is there another way to do that?
Please scuse my English.
Ps. I've searched over many places about this problem, but i can't find a solution.

---

### Post by Gashnark on 2009-07-28
I solve this problem.
I put the configurations in the "/etc/apache2/apache2.conf"
```
<Directory /var/www/FOLDER>
AllowOverride None
AuthType Basic
AuthName "Restricted Files"
AuthUserFile /home/USER/.htpasswds/public_html/FOLDER/passwd
Require user USERNAME
</Directory>

```
But at the end, I cant do it with the .htaccess file.
Anyway thanks for reading!

---

