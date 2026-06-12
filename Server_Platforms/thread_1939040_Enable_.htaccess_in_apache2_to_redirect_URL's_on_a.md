---
title: "Enable .htaccess in apache2 to redirect URL's on a local server?"
date: 2012-03-10
forum: Server Platforms
---

### Post by pythonscript on 2012-03-10
I'm trying to use a .htaccess file to redirect URL's to a front controller on my server, but I'm having trouble enabling .htaccess files. I searched around for a while and found information stating that I should use AccessFileName and AllowOverride in my httpd.conf file, so I attempted using this code:

```

<Directory /var/www/server/public_html>
AccessFileName .htaccess
AllowOverride ALL
</Directory>

```The index.php, i.e. the front controller, is located at  /var/www/server/public_html/index.php

This is the .htaccess code, which works when I modify the domain name and upload it to my online webserver. How do I get this working locally?

```

<IfModule mod_rewrite.c>
RewriteEngine On
RewriteCond $1 !^(index\.php|ajax|css|error|img|js|robots\.txt|favicon\.ico)
RewriteRule ^(.*)$ index.php?url=$1 [PT,L]
</IfModule>

ErrorDocument 401 http://localhost/hospital/public_html/error/401.php
ErrorDocument 403 http://localhost/hospital/public_html/error/403.php
ErrorDocument 404 http://localhost/hospital/public_html/error/404.php

```Thank you!

---

### Post by pythonscript on 2012-03-10
How embarrassing. My edit (adding public_html after server in the .htaccess file) fixed the problem. Apparently I was much too hasty in posting my original question.

---

