---
title: "How do I configure Apache like I did in WAMP?"
date: 2007-05-22
forum: Server Platforms
---

### Post by jingo811 on 2007-05-22
I'm learning WAMP at a night course.  And I'm using Ubuntu Desktop at home so I wanted to have LAMP to work with off school.
I don't know much about LAMP so far I managed to install it with aptitude and things seems to work.  At least Apache and PHP seems to be working when I test my PHP work files:
```
sudo aptitude install php5 apache2 mysql-server
```

But in school the teacher gave us instructions on stuff to configure for Apache's **httpd.conf** file.  Which seems to be an unneccessary file in Linux.  The equivalence seems to be this file am I correct so far?
```
sudo gedit apache2.conf
```

In this **apache2.conf** file I had difficulty finding these lines to configure which worked in **httpd.conf** file:

> Listen 80
> ServerAdmin [email]billgates@hotmail.com[/email]
> DocumentRoot "D:/course/htdocs";
> 
<Directory "C:/Program Files/Apache2.2/>
#...
Options None
#...
AllowOverride None
#...
Order allow,deny
Allow from all
</Directory>

> CustomLog logs/access.log combined

How can I make my Linux Apache access those lines and change it like I could in Windows Apache?

---

### Post by Wim Sturkenboom on 2007-05-22
Just run *grep* over the directory to find the keywords that you're looking for.

There are a couple of config files for Apache in Ubuntu; the one that you're looking for is probably *ports.conf* or similar.
I can not say which files exactly as I don't use Apache under Ubuntu.

[edit]
After rereading your post: write the config files from scratch or copy them from the windows box to the linux box and edit them afterwards.
[/edit]

---

