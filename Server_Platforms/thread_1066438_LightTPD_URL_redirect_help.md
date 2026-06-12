---
title: "LightTPD URL redirect help"
date: 2009-02-10
forum: Server Platforms
---

### Post by dmizer on 2009-02-10
I have migrated from gallery 1 to gallery 2. All that remains is for me to redirect hotlinked image URLs to the new gallery. Gallery 2 is very helpful if you run Apache, but I'm not sure how to make this work with LightTPD.

For hotlinking redirect, Gallery 2 suggests the following .htaccess file addition:
```
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteCond %{REQUEST_FILENAME} !gallery_remote2.php
RewriteRule (.*)$ /gallery2/main.php?g2_controller=migrate.Redirect&g2_path=$1 [QSA]
</IfModule>
```

I'm not sure how to translate that into lighttpd.conf code.

mod_rewrite and mod_redirect are enabled.

Edit:
I already have the following included under url.rewrite:
```
url.rewrite = (
 "^/(.*)/Rewrite.txt$" => "/$1/Works.txt",
 "^/gallery2/v/(\?.+|\ .)?$" => "/gallery2/main.php?g2_view=core.ShowItem",
 "^/gallery2/admin[/?]*(.*)$" => "/gallery2/main.php?g2_view=core.SiteAdmin&$1",
 "^/gallery2/d/([0-9]+)-([0-9]+)/([^\/]+)(\?|\ )?(.*)$" =>
 "/gallery2/main.php?g2_view=core.DownloadItem&g2_itemId=$1&g2_serialNumber=$2&$3",
 "^/gallery2/v/([^?]+)/slideshow.html" =>
 "/gallery2/main.php?g2_view=slideshow.Slideshow&g2_path=$1",
 "^/gallery2/v/([^?]+)(\?|\ )?(.*)$" =>
 "/gallery2/main.php?g2_view=core.ShowItem&g2_path=$1&$3",
 "^/gallery2/c/add/([0-9]+).html" =>
 "/gallery2/main.php?g2_view=comment.AddComment&g2_itemId=$1",
 "^/gallery2/c/view/([0-9]+).html" =>
 "/gallery2/main.php?g2_view=comment.ShowAllComments&g2_itemId=$1",
 "^/gallery2/p/(.+)" =>
 "/gallery2/main.php?g2_controller=permalinks.Redirect&g2_filename=$1",
 "^/key/([^?]+)(\?|\ )?(.*)$" =>
 "/main.php?g2_view=keyalbum.KeywordAlbum&g2_keyword=$1&$3"
 )
```

---

### Post by dmizer on 2009-02-16
Bump please :)

---

