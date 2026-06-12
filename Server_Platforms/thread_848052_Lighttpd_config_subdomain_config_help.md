---
title: "Lighttpd config subdomain config help"
date: 2008-07-03
forum: Server Platforms
---

### Post by xodeus on 2008-07-03
Is this the right way to do?
I want anything else pitstop.bloggr.dk to be pointed to my wpmu site.
My config looks like that, but I can not connect to the 
pitstop.bloggr.dk
I've an DNS A record
> pitstop.bloggr.dk 87.104.16.48 43200
bloggr.dk 87.104.16.48 43200

An my config looks like this:
```
server.modules += ( "mod_rewrite" )


$HTTP["host"] =~ "(^|\.)bloggr\.dk$"{
server.document-root       = "/var/www/bloggrdk"
simple-vhost.default-host = "bloggr.dk"
server.error-handler-404 = "/index.php"
url.rewrite-once = (
    "^/(.*/)?files/$" => "/index.php",
    "^/(.*/)?files/(.*)" => "/wp-content/blogs.php?file=$2",
    "^(/wp-admin/.*)" => "$1",
    "^/([_0-9a-zA-Z-]+/)?(wp-.*)" => "/$2",
    "^/([_0-9a-zA-Z-]+/)?(.*\.php)$" => "/$2",
)
}
$HTTP["host"] =~ "(^|\.)pitstop\.bloggr\.dk$" {
server.document-root = "/var/www/pitstopbloggrdk"
}
```

Do I miss something? My wpmu is working correctly

---

