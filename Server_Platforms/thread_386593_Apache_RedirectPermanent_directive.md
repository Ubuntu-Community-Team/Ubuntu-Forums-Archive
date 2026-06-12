---
title: "Apache RedirectPermanent directive"
date: 2007-03-17
forum: Server Platforms
---

### Post by Ferio on 2007-03-17
Hi, I'm just trying to setup an Apache server to redirect from [http://domainname.com](http://domainname.com) to [http://www.domainname.com](http://www.domainname.com) by modifying *.htaccess*. Since this is my first time doing it, I'm not sure that I'm doing it OK at all. My .htaccess looks like this right now (I've added the bold text):
```

#DirectoryIndex index.php index.html 
#Options +FollowSymLinks 
#RewriteBase /relative/web/path/ 
 
<IfModule mod_rewrite.c> 
 RewriteEngine On 
 RewriteCond %{REQUEST_FILENAME} -f [OR] 
 RewriteCond %{REQUEST_FILENAME} -d 
 RewriteRule ^(.+) - [PT,L] 
  
 RewriteRule ^(.*) index.php 
</IfModule> 

[B]<IfModule mod_alias.c>
 RedirectPermanent http://domainname.com http://www.domainname.com
</IfModule>[/B]
 
#php_value register_globals 0

```
Thanks in advance.

---

### Post by MJN on 2007-03-17
This is what I use, but inside my <Virtualhost></Virtualhost> container in /etc/apache2/sites-available/default:

```

        RewriteEngine On
        RewriteCond %{HTTP_HOST} !^www\.newtonnet\.co\.uk [NC]
        RewriteCond %{HTTP_HOST} !^$
        RewriteRule ^/(.*) http://www.newtonnet.co.uk/$1 [R=301,L]

```

Is there a reason you want/need it in the .htaccess file? I believe there are advantages to not doing so if you've got server config access.

Mathew

---

### Post by Frosty Cold Drink on 2007-03-17
Throwing something like that in .htaccess is handy since you can back up the document root and take your configuration with you.

Otherwise, yes it is better to do it in the regular Apache config files.

By the way, if you want to redirect everything to [www.*](www.*), you should use mod_rewrite like MJN suggests (since you are already using it) and it should be your first RewriteRule (or chain).

---

### Post by Ferio on 2007-03-18
There's no special reason to do it in the *.htaccess* file, I found out that I should do this using a SEO tool, then I googled it, and what I found was an explanation on how to do it like this. This is the first time I modify a live Apache server, and till now, I always followed Ubuntu wiki (to set a LAMP server) since I don't know the needed syntax.

Besides, I can't find the path you posted in my site, maybe I'm not allowed to get there.

---

### Post by Ferio on 2007-03-18
As I've said to MJN, I think I'm not allowed to access these files (I can't find the path he told me).

I don't know how to do it using mod_rewrite (these is my first time modifying a live Apache server and I don't know the syntax), but I'll try to look on it.

---

### Post by Ferio on 2007-03-18
I've found a solution that works:
```

#DirectoryIndex index.php index.html 
#Options +FollowSymLinks 
#RewriteBase /relative/web/path/ 
 
<IfModule mod_rewrite.c> 
 RewriteEngine On
 [B]RewriteCond %{HTTP_HOST} ^domain.com 
 RewriteRule (.*) http://www.domain.com/ [R=301,L][/B]  
 RewriteCond %{REQUEST_FILENAME} -f [OR] 
 RewriteCond %{REQUEST_FILENAME} -d 
 RewriteRule ^(.+) - [PT,L] 
 RewriteRule ^(.*) index.php 
</IfModule> 
 
#php_value register_globals 0

```
Thank you very much!

---

### Post by MJN on 2007-03-18
That's great! Did my rules not work for you?

I would've thought you'd at least want $1 after the domain redirect such that mydomain.com/somefile.htm gets rewritten to [www.mydomain.com/somefile.htm](www.mydomain.com/somefile.htm) rather than dumping them back at the root (which is almost certainly not want the user will want).

Furthermore, it can be handy to have *any* prefix get rewritten e.g. wwww.mydomain.com redirects to [www.mydomain.com](www.mydomain.com) this way typos of www are also covered (besides more).

Mathew

---

### Post by Ferio on 2007-03-18
Hmmm, so that's what the $1 was for... Don't ask me why, but I deleted it. Now it's there again, thank you for the advice.

---

