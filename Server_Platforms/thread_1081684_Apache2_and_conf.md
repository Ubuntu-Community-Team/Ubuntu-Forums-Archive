---
title: "Apache2 and conf"
date: 2009-02-26
forum: Server Platforms
---

### Post by Cl0cKw0rK on 2009-02-26
For some reason i cannot get .htaccess working
i have the required things set up as i think they should be.
.htaccess
```

AuthUserFile /var/www/.htpasswd
AuthName "EnterPassword"
AuthType Basic

Require valid-user

```
and the apache2.conf (pertinent parts)
```

AccessFileName .htaccess

<Directory /mnt/raid/programs>
     AllowOverride AuthConfig
     Options Indexes FollowSymLinks Includes
     Order Allow,Deny
     Allow from all
</Directory>

```

I can access the file fine with no login prompt
Just testing, i made the apace2.conf say
```

AccessFileName .htaccess

<Directory />
     AllowOverride none
     Options Indexes FollowSymLinks Includes
     Order Deny,Allow
     Deny from all
</Directory>

```
and i was still able to access it fine.
Any help on what im doing wrong?
Thanks,
~Clockwork

---

### Post by E_K on 2009-02-26
> AuthTyoe Basic


typo?

authtype basic?

---

### Post by Cl0cKw0rK on 2009-02-26
yep, typo, edit so thats it right(was not copy-pasted)

---

### Post by Cl0cKw0rK on 2009-02-28
bump.

---

### Post by Cl0cKw0rK on 2009-02-28
Would something change if I use a SymLink to get to that folder?

---

### Post by Cl0cKw0rK on 2009-02-28
Ok, i can run ssi based on a <directory> tag, so apache is definetly parsing it.
anybody out there can help me?

---

### Post by albinootje on 2009-02-28
> **Cl0cKw0rK said:**
> For some reason i cannot get .htaccess working

Here's my working htaccess config :

My .htaccess file :
```

AuthType Basic
AuthName "Restricted Access"
AuthUserFile /home/secure-apache/apasswords
Require user myusername

```
And I'm only using the userdir module for htaccess :
```

<IfModule mod_userdir.c>
        UserDir public_html
        UserDir disabled root

        <Directory /home/*/public_html>
                AllowOverride AuthConfig
                Options MultiViews Indexes SymLinksIfOwnerMatch IncludesNoExec
        </Directory>
</IfModule>

```

---

### Post by albinootje on 2009-02-28
And I've created the user with something like :
sudo htpasswd -c /home/secure-apache/apasswords myusername

---

