---
title: "apache NameVirtualHost problem"
date: 2009-09-15
forum: Server Platforms
---

### Post by lavacano on 2009-09-15
I have

```
## Virtual host VirtualDocumentRoot

NameVirtualHost 67.160.90.57:80
        <VirtualHost 67.160.90.57:80>
	ServerName chads-computers.com
        DocumentRoot /var/www/www.chads-computers.com
        Options All                    
        #ServerAdmin admin@example.com 
        # Store uploads in /var/www/wp-uploads/chads-computers.com
        RewriteEngine On                         
        RewriteRule ^/wp-uploads/(.chads-computers.com)$ /var/www/wp-uploads/%{HTTP_HOST}/$1
        </VirtualHost>



        <VirtualHost 67.160.90.57:80>
	ServerName www.chads-computers.com
        DocumentRoot /var/www/www.chads-computers.com
        Options All                    
        #ServerAdmin admin@example.com 
        # Store uploads in /var/www/wp-uploads/chads-computers.com
        RewriteEngine On                         
        RewriteRule ^/wp-uploads/(.chads-computers.com)$ /var/www/wp-uploads/%{HTTP_HOST}/$1
        </VirtualHost>



        <VirtualHost 67.160.90.57:80>
	ServerName mike.chads-computers.com
        DocumentRoot /usr/share/gallery2
        Options All                    
        #ServerAdmin admin@example.com                        
        </VirtualHost>

```

but when i try mike.chads-computers.com it spits a 302 found and shoots me to the root of /var/www/chads-computers it should shoot me to /usr/share/gallery2

```
mike.chads-computers.com:80 67.160.90.57 - - [15/Sep/2009:20:24:23 -0700] "GET / HTTP/1.1" 302 342 "-" "Opera/9.80 (X11; Linux x86_64; U; en) Presto/2.2.15 Version/10.00"
```

---

### Post by lavacano on 2009-09-16
nevermind script was misconfigured on gallery.

---

