---
title: "Apache2 virtual hosts help"
date: 2011-02-06
forum: Server Platforms
---

### Post by Nova 107 on 2011-02-06
Im trying to configure a virtual host on my machine but all the tutorials I'm finding seem to be a bit fragmented and incomplete. I know that I have to do the configuring but I'm not exactly sure what to configure.

---

### Post by rudelgurke on 2011-02-06
And where exactly is the problem ?

[http://httpd.apache.org/docs/2.2/vhosts/](http://httpd.apache.org/docs/2.2/vhosts/)

Pretty much sums it up.

---

### Post by Nova 107 on 2011-02-06
I dont understand this, theres too much on these pages with far too little instruction. I set up my httpd.conf the way it says, but when I restart apache it tells me that the documentroots do not exist.

---

### Post by Nova 107 on 2011-02-06
Ok, I managed to get one of the virtual hosts working, but the other still doesn't work. The configuration files for each site are almost exactly the same with the only difference being the names, but the second site cannot be found.

---

### Post by James78 on 2011-02-07
Please post your configuration files in [CODE] tags.

---

### Post by elico on 2011-02-07
did you try this thing?
[http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)

---

### Post by Nova 107 on 2011-02-07
> **elico said:**
> did you try this thing?
[http://httpd.apache.org/docs/2.2/vhosts/name-based.html](http://httpd.apache.org/docs/2.2/vhosts/name-based.html)
 
I added this to my httpd.conf and it didnt work, then I found that I had to create a new configuration for each site which I set up like this: 
 
```

<VirtualHost *:80>
ServerName [www.mywebsite.tk]("http://www.mywebsite.tk")
ServerAlias *mywebsite.tk
DocumentRoot /var/www/mywebsite
</VirtualHost>

```
 
My other site is set up the same way with the changes made for the diferent sites and folders. The first one I set up works, but the second one doesnt.

---

### Post by cariboo on 2011-02-07
If you are using a recent version of Ubuntu server, http.conf isn't used anymore, the way it's done now is to set up your virtual web sites in /etc/apache2/sites-available, then when you have set it up to your liking, use a2ensite to enable the site.

This [page]("http://www.debian-administration.org/articles/412"), may be more relevant

---

