---
title: "Website not resolving without www"
date: 2009-10-12
forum: Server Platforms
---

### Post by serlex on 2009-10-12
Hosting problem:

website on [www.example.com](www.example.com) resolvs to correct directory but example.com doesn't 

URL [http://example.com](http://example.com) directs to /var/www/ and not /var/www/example.com

/etc/apache2/sites-enabled/example.com

```
<VirtualHost *:80>
        #Basic setup
        ServerAdmin admin@example.com
        ServerName www.example.com
        ServerAlias example.com *.example.com
        DocumentRoot /var/www/example.com
        <Directory /var/www/example.com>
                Order Deny,Allow
                Allow from all
                # Don't show indexes for directories
                Options All Indexes FollowSymLinks MultiViews -Indexes
                #Options -Indexes
        </Directory>
```

DNS:
```
www.example.com  	A    	89.200.137.184  	
*.example.com 	        A 	89.200.137.184 	
mail.example.com 	A 	89.200.137.184 	
www.example.com 	CNAME 	example.com	

```

Any ideas?

---

### Post by nandemonai on 2009-10-12
EDIT:

Disregard.

I need new glasses ;)

---

### Post by kemra on 2009-10-13
OK so webservers aren't quite my thing but I thought I'd put forward a suggestion. Where you have the following in DNS and /etc/apache2/sites-enabled/example.com:

```
*.example.com
```

try changing it to:

```
*example.com
```

It may be that these files are expecting a period before example.com due to your current configuration so this *may* solve your problems.

---

