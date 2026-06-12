---
title: "Help with URL Rewrites Gallery2 on ISPConfig Ubuntu 8.10"
date: 2009-03-01
forum: Server Platforms
---

### Post by DantePasquale on 2009-03-01
Hi All,

I would really like to get URL rewrites working to utilize Gallery2 Permalinks, but can't seem to figure out what my problem is. Here's my configuration:
```

Gallery version = 2.2.6 core 1.2.0.8
PHP version = 5.2.6-2ubuntu4.1 apache2handler
Webserver = Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch mod_ssl/2.2.9 OpenSSL/0.9.8g
Database = mysqli 5.0.67-0ubuntu6, lock.system=flock
Toolkits = Dcraw, Exif, Ffmpeg, Getid3, LinkItemToolkit, NetPBM, Thumbnail, Gd, ArchiveUpload, SquareThumb
Acceleration = none, none
Operating system = Linux inferno.cocoanet.us 2.6.27-12-generic #1 SMP Thu Feb 5 09:26:42 UTC 2009 x86_64
Default theme = matrix
gettext = enabled
Locale = en_US
Browser = Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.0.6) Gecko/2009020911 Ubuntu/8.10 (intrepid) Firefox/3.0.6
Rows in GalleryAccessMap table = 18
Rows in GalleryAccessSubscriberMap table = 2
Rows in GalleryUser table = 2
Rows in GalleryItem table = 1
Rows in GalleryAlbumItem table = 1
Rows in GalleryCacheMap table = 0 
```

I setup the URL rewrite plugin in my codebase [http://gallery.cocoanet.us]("http://gallery.cocoanet.us") and it works fine, but it's an empty gallery.

Here's the .htaccess
```
# BEGIN Url Rewrite section
# (Automatically generated.  Do not edit this section)
<IfModule mod_rewrite.c>
    RewriteEngine On

    RewriteBase /

    RewriteCond %{REQUEST_FILENAME} -f [OR]
    RewriteCond %{REQUEST_FILENAME} -d [OR]
    RewriteCond %{REQUEST_FILENAME} gallery\_remote2\.php
    RewriteCond %{REQUEST_URI} !/main\.php$
    RewriteRule .   -   [L]

    RewriteCond %{QUERY_STRING} g2_view=core.DownloadItem
    RewriteCond %{QUERY_STRING} g2_itemId=([0-9]+)
    RewriteCond %{HTTP:Referer} !^[a-zA-Z0-9\+\.\-]+://www.cocoanet.us/   [NC]
    RewriteCond %{HTTP:Referer} !^[a-zA-Z0-9\+\.\-]+://gallery.cocoanet.us/   [NC]
    RewriteCond %{HTTP:Referer} !^$
    RewriteRule .   /main.php?g2_view=watermark.DownloadItem&g2_itemId=%1   [L]
    RewriteCond %{THE_REQUEST} /d/([0-9]+)-([0-9]+)/([^/?]+)(\?.|\ .)
    RewriteCond %{REQUEST_URI} !/main\.php$
    RewriteRule .   /main.php?g2_view=core.DownloadItem&g2_itemId=%1&g2_serialNumber=%2&g2_fileName=%3   [QSA,L]
    RewriteCond %{THE_REQUEST} /v/([^?]+)(\?.|\ .)
    RewriteCond %{REQUEST_URI} !/main\.php$
    RewriteRule .   /main.php?g2_path=%1   [QSA,L]
    RewriteCond %{THE_REQUEST} /f/([^?]+)(\?.|\ .)
    RewriteCond %{REQUEST_URI} !/main\.php$
    RewriteRule .   /main.php?g2_controller=permalinks.Redirect&g2_filename=%1   [QSA,L]
</IfModule>

# END Url Rewrite section
```

But, when I enabled the plugin in my multi-sites, I immediately get 500 errors, Page not Found. Like part of Gallery understands the rewrite (or Apache) but part of Gallery is not recognizing it -- or something.

Here's the .htaccess from a multisite:

```
# BEGIN Url Rewrite section
# (Automatically generated.  Do not edit this section)
<IfModule mod_rewrite.c>
    Options +FollowSymlinks
    RewriteEngine On

    RewriteBase /gallery/

    RewriteCond %{REQUEST_FILENAME} -f [OR]
    RewriteCond %{REQUEST_FILENAME} -d [OR]
    RewriteCond %{REQUEST_FILENAME} gallery\_remote2\.php
    RewriteCond %{REQUEST_URI} !/gallery/main\.php$
    RewriteRule .   -   [L]

    RewriteCond %{HTTP:Authorization} (.+)
    RewriteCond %{QUERY_STRING} !g2_authorization=
    RewriteRule .   %{REQUEST_URI}?g2_authorization=%1   [QSA]
    RewriteCond %{THE_REQUEST} /gallery/d/([0-9]+)-([0-9]+)/([^/?]+)(\?.|\ .)
    RewriteCond %{REQUEST_URI} !/gallery/main\.php$
    RewriteRule .   /gallery/main.php?g2_view=core.DownloadItem&g2_itemId=%1&g2_serialNumber=%2&g2_fileName=%3   [QSA,L]
    RewriteCond %{THE_REQUEST} /gallery/v/([^?]+)(\?.|\ .)
    RewriteCond %{REQUEST_URI} !/gallery/main\.php$
    RewriteRule .   /gallery/main.php?g2_path=%1   [QSA,L]
</IfModule>
```

Help! Oh, my code for the multisite is in [http://www.cocoanet.us/gallery]("http://www.cocoanet.us/gallery"). So the Rewritebase /gallery/ looks OK to me.

How can I debug something like this?

Danté

---

