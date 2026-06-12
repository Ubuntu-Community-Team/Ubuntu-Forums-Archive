---
title: "Ubuntu 14 and apache 2.4 ( you guessed it, Virtualhosts)"
date: 2014-07-12
forum: Server Platforms
---

### Post by LoganGuy on 2014-07-12
I have tried using virtual hosts on two separate virtualbox ubuntu 14 installations and I can't make it work.  I've tried everything on the web.  The web directory I am trying to use is  /web/virtual/weba.com .  I edited apache2.conf and inserted:[INDENT=2]<Directory /web/virtual/weba.com/>    I have tried omiting /weba.com and it does not work either way.[/INDENT]
[INDENT=2]    Options Indexes FollowSymLinks[/INDENT]
[INDENT=2]    AllowOverride None[/INDENT]
[INDENT=2]    Require all granted[/INDENT]
[INDENT=2]</Directory>[/INDENT]
I gave www-data ownership and read/write to /web and all subdirectories
I created a file called weba.com.conf in the sites-available folder and here are the contents of that file:[INDENT=2]listen 127.0.0.1:80[/INDENT]
[INDENT=2]
[/INDENT]
[INDENT=2]<VirtualHost *:80>[/INDENT]
[INDENT=2]    ServerAdmin [EMAIL="admin@example.com"]admin@example.com[/EMAIL][/INDENT]
[INDENT=2]    ServerName weba.com[/INDENT]
[INDENT=2]    ServerAlias [www.weba.com]("http://www.weba.com")[/INDENT]
[INDENT=2]    DocumentRoot /web/virtual/weba.com[/INDENT]
[INDENT=2][COLOR=#0000cd]        <Directory />                                           I have tried it with and without the <Directory entry.[/COLOR][/INDENT]
[INDENT=2][COLOR=#0000cd]                Options All[/COLOR][/INDENT]
[INDENT=2][COLOR=#0000cd]                AllowOverride All[/COLOR][/INDENT]
[INDENT=2][COLOR=#0000cd]                Require all granted[/COLOR][/INDENT]
[INDENT=2][COLOR=#0000cd]        </Directory>[/COLOR][/INDENT]
[INDENT=2]    ErrorLog ${APACHE_LOG_DIR}/error.log[/INDENT]
[INDENT=2]    CustomLog ${APACHE_LOG_DIR}/access.log combined[/INDENT]
[INDENT=2]</VirtualHost>[/INDENT]
[INDENT]
I created a simple index.html file in /web/virtual/weba.com/index.html

I ran 
sudo a2dissite weba.com
sudo a2ensite weba.com
service apache2 reload

I added 127.0.0.1      weba.com to the hosts file.
I cleared the chrome cache

If I go to [http://weba.com](http://weba.com)  I get the default apache 2 index fiile

[SIZE=5]What is wrong here????
[/SIZE]regards

[/INDENT]

---

### Post by SeijiSensei on 2014-07-13
1) Remove the listen on 127.0.0.1.  You should be using the *:80 syntax as your <VirtualHost> declaration does.

2) Create new <Directory> stanzas for each of the DocumentRoot directories, e.g.,
```

DocumentRoot /web/virtual/weba.com
<Directory "/web/virtual/weba.com">
Options All
AllowOverride All
</Directory>

```

3) Make sure the execute permission is set on all directories above the DocumentRoot.  

4) Examine /var/log/error.log for additional details.

---

