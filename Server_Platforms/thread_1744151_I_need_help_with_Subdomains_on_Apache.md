---
title: "I need help with Subdomains on Apache"
date: 2011-04-30
forum: Server Platforms
---

### Post by AdamTheComputerGeek on 2011-04-30
[CENTER][B][SIZE=4]I need help

[/SIZE][/B][LEFT][B]Hello, _Ubuntu Forums_! I need some help here. I am running a site called World Wide Web.cX

The address of the site is [http://worldwideweb.cx.cc/](http://worldwideweb.cx.cc/)

I *don't *want to post any content until I get my wiki running, which I want on a subdomain.

I am trying every way to get my subdomain working.

Here are my specs--

Apache HTTP Web Server: [/B]Apache/2.2.17 

**Operating System:** Ubuntu 11.04 Natty Narwhal

[B]Here are the files I made...

[/B]```
NameVirtualHost *:80
<VirtualHost *:80>
ServerName wiki.worldwideweb.cx.cc
ServerAdmin Windows7Freak@live.com
DocumentRoot /var/www/wiki/
<Directory /var/www/wiki/>
Options Indexes FollowSymLinks MultiViews
#AllowOverride None
AllowOverride All
Order allow,deny
allow from all
</Directory>
</VirtualHost>
```

That is my file I enabled in Sites-enabled. Its the file for the wiki.worldwideweb.cx.cc domain.

That's all I edited. When I type in wiki.worldwideweb.cx.cc it just says this domain is available and ads. Also, I try making a CNAME record

HOST: wiki.worldwideweb.cx.cc
TYPE: CNAME
VALUE: wiki.worldwideweb.cx.cc

and it still doesnt work.

How can I make my subdomain work?
[/LEFT]
[/CENTER]

---

### Post by falko on 2011-04-30
Do you own the domain worldwideweb.cx.cc?

> HOST: wiki.worldwideweb.cx.cc
TYPE: CNAME
VALUE: wiki.worldwideweb.cx.cc
Value should be worldwideweb.cx.cc.

---

