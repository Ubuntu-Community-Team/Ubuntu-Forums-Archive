---
title: "virtualhosts weired problem !"
date: 2010-02-23
forum: Server Platforms
---

### Post by mazid on 2010-02-23
hello, 

i'm trying to host 2 sites on ubuntu 8.04, after installing apache2 i configure virtual hosts as i could 
site1 : /etc/apache2/sites-available/site1.com

```
<VirtualHost *:80>
ServerName www.site1.com
  ServerAlias site1.com *site1.com
  ServerAdmin admin@localhost
DocumentRoot /some/path
  CustomLog /var/log/apache2/site1-access.log combined
  ErrorLog /var/log/apache2/site1-error.log
</VirtualHost>
```

site2 :/etc/apache2/sites-available/site.com

```
<VirtualHost *:80>
ServerName www.site2.com
  ServerAlias site2.com *site2.com
  ServerAdmin admin@localhost
DocumentRoot /some/path
  CustomLog /var/log/apache2/site2-access.log combined
  ErrorLog /var/log/apache2/site2-error.log
</VirtualHost>
```

well the thing is when i try to access site with site1.com or site2.com they work just fine 
but i can get them to work **www**.site1.com and **www**.site2.com !! 

any idea, any help with that ?

---

### Post by windependence on 2010-02-23
If you are accessing them from outside the network, you will need to set up a cname for www.<yoursite.com>.

-Tim

---

