---
title: "apache2 redirects"
date: 2008-08-28
forum: Server Platforms
---

### Post by sparkles on 2008-08-28
I'm serving a couple of websites using apache 2.0.53. 1 of them wants to have a new site with a different domain that is exactly the same as their current site except for the main page. I have already specified the new domain using ServerAlias in the apache conf. I will setup the A record for the new domain to point to the same ip address.

I know I can simply perform different behaviour in index.php based on $_SERVER['SERVER_NAME']. What I was wondering is if there's some way, maybe using AliasMatch or RewriteRule, to redirect visitors to index2.php initially instead of index.php.

TIA

---

### Post by windependence on 2008-08-28
Actually it's easier in php to do this. I'll have to dig up the code I used and post it here.

-Tim

---

### Post by windependence on 2008-08-28
The following php script redirects the user to /index.php within the same site: 



[PHP]<? header('Location: /index.php'); ?>[/PHP]

-Tim

---

### Post by mbeach on 2008-08-28
haven't tried a directoryindex in a vhost file, but I'd give it a try to see if it does the trick.
```

<VirtualHost *>
ServerName yournewsite.com
ServerAdmin admin@yournewsite.com
DocumentRoot /var/www/youroldsite
.
.
.
DirectoryIndex index2.php index.html
.
.
.

</VirtualHost>
```

---

