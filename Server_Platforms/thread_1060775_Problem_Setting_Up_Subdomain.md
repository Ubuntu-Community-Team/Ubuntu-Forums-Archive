---
title: "Problem Setting Up Subdomain"
date: 2009-02-05
forum: Server Platforms
---

### Post by mike_g on 2009-02-05
I want to setup a subdomain, but, either I am missing something, or I got something wrong. The domain is already setup. To create the subdomain I appended this to Apache's httpd.conf:
```
<VirtualHost *:80>
    ServerName test.mydomain.com
    ServerAlias www.test.mydomain.com
    DocumentRoot /var/www/mydomaindirectory
    <Directory "/var/www/mydomaindirectory">
       AllowOverride All
       DirectoryIndex index.php
    </Directory>
</VirtualHost>
```
but whenever i point my browser to test.mydomain.com it redirects me to mydomain.com. What am I missing here? Oh, and ther server is actually running fedora, but I doubt that makes much difference.

Cheers.

---

