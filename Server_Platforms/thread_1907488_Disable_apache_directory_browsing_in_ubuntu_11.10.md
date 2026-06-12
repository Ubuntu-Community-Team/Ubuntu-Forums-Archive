---
title: "Disable apache directory browsing in ubuntu 11.10"
date: 2012-01-11
forum: Server Platforms
---

### Post by peprex on 2012-01-11
Hi,
 
I have a server with a 40.40.40.40 ip. When I access to [http://40.40.40.40](http://40.40.40.40) it lists my virtual hosts directories. I do not want him to do that !
 
I followed several tutorials but no one works for me. Many of them tell me to change the **Options Indexes FollowSymLinks MultiViews** line in the httpd.conf file for **Options FollowSymLinks MultiViews **(remove the Indexes option).
 
The problem ? httpd.conf is blank. So I get to apache2.conf (intuition , not knowledge) and the line was not there. 
 
Any ideas ? Please help.
 
Thanks in advance !

---

### Post by Lars Noodén on 2012-01-11
Look in /etc/apache2/sites-available/default

httpd.conf is not used anymore and apache2.conf is for global settings, not vhost-specific settings.

---

### Post by peprex on 2012-01-11
You were right !
 
I removed the word Indexes everytime it appears on the default config file in the sites-available folder and also from my virtuals. So when I get to [http://40.40.40.40](http://40.40.40.40) I get a 403 forbidden.
 
Lots of thanks !

---

### Post by chuck97224 on 2013-02-13
To disable directory browsing:
```

sudo a2dismod autoindex
sudo service apache2 restart

```
Tested on 12.10

---

