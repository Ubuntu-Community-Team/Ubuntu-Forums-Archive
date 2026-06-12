---
title: "LAMP images slow"
date: 2011-12-05
forum: Server Platforms
---

### Post by amainejr on 2011-12-05
I seem to be having an issue with slow loading images.  Thought it may have been a mod_rewrite issue, but it happens even when accessing an image directly.  The log files show no evidence of errors and access logs report back what I would expect when accessing an image.

It doesn't happen on every image, and most of them load quite quickly.  I'm actually running two different servers that are experiencing the exact same problems.  I've setup memcached, increased Apache's SendBufferSize directive, slightly modded the mpm-prefork server limits, and a couple of other things, trying to get the load times of these images down.  While the rest of the server has sped up, these images seem to not give a crap what directives I give my server.

I read that it could be an issue with the uploading process, about filezilla possibly sending the image files up as ASCII instead of Binary, but testing hasn't proven that one bit.

Relative configurations:

```

#apache.conf

Timeout 300
KeepAlive On
MaxKeepAliveRequests 100
KeepAliveTimeout 15

<IfModule mpm_prefork_module>
    StartServers         15
    MinSpareServers      10
    MaxSpareServers      20
    ServerLimit          512
    MaxClients           512
    MaxRequestsPerChild   0
    SendBufferSize      16384
</IfModule>

User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

AccessFileName .htaccess

<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>

DefaultType text/plain
HostnameLookups Off


```

```

#.htaccess

<IfModule mod_rewrite.c>
  Options +FollowSymLinks
  RewriteEngine On

  # Get rid of index.php
  RewriteCond %{REQUEST_URI} /index\.php
  RewriteRule (.*) index.php?rewrite=2 [L,QSA]

  # Rewrite all directory-looking urls
  RewriteCond %{REQUEST_URI} /$
  RewriteRule (.*) index.php?rewrite=1 [L,QSA]

  # Try to route missing files
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} public\/ [OR]
  RewriteCond %{REQUEST_FILENAME} \.(flv|htm|html|php|css|js)$
  RewriteRule . - [L]

  # If the file doesn't exist, rewrite to index
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteRule ^(.*)$ index.php?rewrite=1 [L,QSA]

</IfModule>

# sends requests /index.php/path/to/module/ to "index.php"
# AcceptPathInfo On

# @todo This may not be effective in some cases
FileETag Size

```

```

#mods enabled

alias
auth_basic
authn_file
authz_default
authz_groupfile
authz_host
authz_user
autoindex
cgi
deflate
dir
env
mime
negotiation
php5
reqtimeout
**rewrite**
setenvif
status

```


```

#access.log

[05/Dec/2011:11:49:17 -0500] 
"GET /public/album_photo/1000000/1000/2/2801.jpg?c=3ab4 
HTTP/1.1" 200 33771 "http://xxx.xxx.xxx.xxx/albums/photo/view/album_id/1/photo_id/2" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:8.0) Gecko/20100101 Firefox/8.0"

[05/Dec/2011:12:02:58 -0500] 
"GET /public/album_photo/1000000/1000/2/2801.jpg 
HTTP/1.1" 200 33772 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64; rv:8.0) Gecko/20100101 Firefox/8.0"

```


The first request was completed by a page click, while the other a direct link typed into the address bar.  I see that the first one uses the rewrite rule, while the second does not.  In both scenarios, the files load slowly.  I've tried replacing apache's DefaultType directive with application/octet-stream, but that doesn't work either.

Any thoughts?

---

### Post by amainejr on 2011-12-05
After some more testing, I've found that Apache eats up an entire processor while a request goes through.  Once that page has loaded, you can click to another page and it eats up the processor again.  However, if you revisit either of the two pages within a couple of minutes, the processor is barely tapped and the pages load almost instantly.  Caching configuration problem, maybe?

---

### Post by amainejr on 2011-12-05
I think I've found the culprit.  There were reports in the apache error log reporting that favicon.ico wasn't found.  I didn't think this would be a cause for concern, but it got reported around 10 times per request.  Uploaded a favicon.ico file to the server and the problem ceased.  Server load fell from 100% down to about 3% per click.

What's the deal with that?

---

