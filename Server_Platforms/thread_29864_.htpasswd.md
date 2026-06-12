---
title: ".htpasswd"
date: 2005-04-26
forum: Server Platforms
---

### Post by PeteG on 2005-04-26
Hi,

I've tried creating .htpasswd and .htaccess in order to restrict access to a file on the server. The folder called downloads is located in /var/www/downloads. So i've tried creating the .htpasswd file in that directory (cd to /var/www/downloads then htpasswd -c .htpasswd username) and i've also tried creating the htpasswd file in /etc/apache2. Nothing seems to work at all. The .htaccess from /var/www/downloads reads:
AuthType Basic
AuthName "Restricted Files"
AuthUserFile /etc/apache2
Require user username

I'm using the apache server that i got through apt-get. Any help would be awesome. Thanks.

Pete.

P.S. I've got webmin installed and it says that mod_auth is active however when looking in /etc/apache2/mods-enabled i can't see it in there. Could this be it? It's not in mods-available either.

---

### Post by hgibson on 2005-04-26
The ".htpasswd" is used in conjunction with the ".htaccess" file.

The ".htaccess" limits access to a directory/folder that is available via your web server.

You need to create the ".htaccess" file in the folder you want to limit access to.
For example:

 cd /var/www/html
 touch .htaccess

The content of the file specifies where to get the password for the allowed users.

An example file:

 AuthUserFile /var/www/html/.htpasswd
 AuthName "Authorization Required"
 AuthType Basic
 require valid-user

To create the initial .htpasswd file you must use the -c flag. As root run:

 htpasswd -c /var/www/html/.htpasswd username

Now read the man page about ".htpasswd" to be able to create more authorised users.

Type:

 man htpasswd

Hope this brief tutorial gives you an idea what to do.
Be sure to setup the correct settings for authorisation in your apache configuration too.

---

### Post by PeteG on 2005-04-26
Thanks for the tutorial however as stated in my original post i've already tried this.

Pete.

---

### Post by LeNain on 2005-04-26
Well, you didn't exactly do as hgibson told in his tutorial
 
You htaccess file looks like this
[i]AuthType Basic
AuthName "Restricted Files"
AuthUserFile /etc/apache2
Require user username
[/i]
 
His looks like that
 
[i]AuthUserFile [color=red]/var/www/html/.htpasswd
[/color]AuthName "Authorization Required"
AuthType Basic
require valid-user[/i]
 
As you might notice, you don't need only the path where the file belongs to, but the [color=red]**full path**[/color] of the file itself

---

### Post by alastair on 2005-04-26
I don't even think that the "AuthUserFile" should be under the WWW root (/var/www/html I assume).

But - as people say, it /should/ be the user/pass file

e.g.

AuthUserFile /etc/apache2/my_users

---

### Post by PeteG on 2005-04-27
Ok. I've completely tried what was in the tutorial above still with no luck. I've tried putting the .htpasswd file in /etc/apache2/ also however that didn't work. I made sure to point exactly to the .htpasswd file in the AuthUserFile. It must be something to do with configuring the apache2 configuration. However in webmin it states that i have mod_auth on. I can't see it in the mods-enabled though. I was wondering if this could be it?

Pete.

---

### Post by heimo on 2005-04-27
You may need to use AllowOverride directive (in your site-specific conf or apache2 global configuration file)
[http://httpd.apache.org/docs-2.0/mod/mod_auth.html]("http://httpd.apache.org/docs-2.0/mod/mod_auth.html")
[http://httpd.apache.org/docs-2.0/mod/core.html#allowoverride]("http://httpd.apache.org/docs-2.0/mod/core.html#allowoverride") 
 
Something like AllowOverride Authconfig. See that it's in correct place. This directive defines what you can do with .htaccess file (you can also change the name of that file, by default it's .htaccess). You could also make the change in config file instead of using. .htaccess files.

---

### Post by rwabel on 2005-05-07
```
sudo vim /etc/apache2/apache2.conf
``` 

then add that to the file

 ```
<Directory /var/www/downloads>
AllowOverride All
</Directory>
``` 

good luck

---

### Post by LordHunter317 on 2005-05-07
No, don't do a blind AllowOverride all.

Here's a few things:


[list]
[*]Never, ever put a .htpasswd file inside the directories you serve off the web. If you accidently misconfigure your server, it's a good way to get all your passwords compromised.
[*]Don't put in it /etc/apache2 either, unless it's global. Create a directory like /etc/apache2/passwords, and have it's structure mirror your webroot. So you'd create /etc/apache2/passwords/downloads.htpasswd. Don't give anyone but root and the apache user (www-data) access to those directories. Put the file there.
[*]Don't blindly give full override to any directory unless you need it. Instead of what rwabel recommends, use this, which won't require as aggressive permissions:```
<Directory /var/www/downloads>
 
  AllowOverride AuthConfig
 
</Directory>
```However, the better solution is to not use .htaccess at all and put the commands you would put in there in the main apache configuration like so:```
<Directory /var/www/downloads>
 
AllowOverride None
 
AuthType Basic
 
AuthName "Restricted Files"
 
AuthUserFile /etc/apache2/passwords/downloads.htpasswd
 
Require user username
 
</Directory>
```This has the benefit of being slightly faster. OTOH, it means you have to manually reload the server if you change anything. However, the preferred way to do things is via the configuration files and .htaccess wherever possible. Also, hopefully you're placing this in a file specific to this virtualhost and not in the master apache2.conf or httpd.conf.
[*]The mod_auth DSO is compiled into the Apache executable and is always running.
[/list]

---

