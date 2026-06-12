---
title: "Problem with Multiple Hosts in Apache2"
date: 2013-01-10
forum: Server Platforms
---

### Post by novatec1 on 2013-01-10
I have an apache2 server that has been used to host one virtual site. I tried a add a second site (site2) but after creating the second virtual host it shows site1. Each site works independently as long as the other sites virtual host code is commented out. Any help is greatly appreciated. The code is as follows:
 
NameVirtualHost *:80
 
<VirtualHost site1.com:80>
 ServerName site1.com
 DocumentRoot /home/design/vhosts/site1.com/htdocs
 ServerAlias [http://www.site1.com](http://www.site1.com)
  </VirtualHost>

 
<VirtualHost site2.com:80>
 ServerName site2.com
 DocumentRoot /home/design/vhosts/site2.com/htdocs
 ServerAlias [http://www.site2.com](http://www.site2.com)
 </VirtualHost>

---

### Post by SeijiSensei on 2013-01-11
The entry inside <VirtualHost> must match the entry in NameVirtualHost exactly.  So just replace 

```
<VirtualHost site1.com:80>
```

with 

```
<VirtualHost *:80>
```

Apache determines which site's content to display based on the ServerName directive, not the entry in <VirtualHost>.

---

