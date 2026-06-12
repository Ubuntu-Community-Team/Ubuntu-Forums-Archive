---
title: "Apache mod_deflate Problems"
date: 2011-02-10
forum: Server Platforms
---

### Post by LPomfrey on 2011-02-10
Hi,

I'm having some trouble with Apache (running a Django app) and mod_deflate, namely that nothing seems to be getting gzipped by Apache.

Django's dynamic pages are being compressed by Django's GzipMiddleware, but all CSS/JS/etc. media files served by Apache aren't.

Here's my VirtualHost configuration (emails/paths/etc. replaced):
```

<VirtualHost *:80>
    ServerName  example.org
    ServerAlias  example.org

    ServerAdmin   webmaster@example.org

    ServerSignature  Off

    CustomLog  /var/log/apache2/example.org-access.log combined
    ErrorLog  /var/log/apache2/example.org-error.log
    LogLevel warn

    <IfModule mod_deflate.c>

        AddOutputFilterByType DEFLATE text/plain
        AddOutputFilterByType DEFLATE text/html
        AddOutputFilterByType DEFLATE text/xml
        AddOutputFilterByType DEFLATE text/css
        AddOutputFilterByType DEFLATE text/x-js
        AddOutputFilterByType DEFLATE application/xml
        AddOutputFilterByType DEFLATE application/xhtml+xml
        AddOutputFilterByType DEFLATE application/rss+xml
        AddOutputFilterByType DEFLATE application/javascript
        AddOutputFilterByType DEFLATE application/x-javascript
        AddOutputFilterByType DEFLATE application/ecmascript
        AddOutputFilterByType DEFLATE application/x-js

        DeflateCompressionLevel 9

        BrowserMatch ^Mozilla/4 gzip-only-text/html
        BrowserMatch ^Mozilla/4\.0[678] no-gzip
        BrowserMatch \bMSIE !no-gzip !gzip-only-text/html

        <IfModule mod_headers.c>
            Header append Vary Accept-Encoding
            Header append Vary User-Agent env=!dont-vary
        </IfModule>

        DeflateFilterNote Input input_info
        DeflateFilterNote Output output_info
        DeflateFilterNote Ratio ratio_info
        LogFormat '"%r" %{output_info}n/%{input_info}n (%{ratio_info}n%%)' deflate
        CustomLog /var/log/apache2/deflate_log deflate

    </IfModule>

	Alias /media/  /path/to/django/project/media/
    Alias /admin-media/  /path/to/django/project/admin-media/
    Alias /favicon.ico /path/to/django/project/media/img/favicon.ico

    <LocationMatch "/media/(c|j)/">
        ErrorDocument 404 " "
        ExpiresActive on
        ExpiresDefault "access plus 10 years"
        FileETag none
    </LocationMatch>
    <Location /media/img/>
        ExpiresActive on
        ExpiresDefault "access plus 7 days"
        ErrorDocument 404 " "
    </Location>
   
    WSGIScriptAlias  /  /path/to/django/project/apache/django.wsgi

    <IfModule mod_mem_cache.c>
        CacheEnable mem /
        MCacheSize 10240
    </IfModule> 

</VirtualHost>

```

For some reason when looking through the deflate log all I get is "-" where there should be numbers like:
```

"GET / HTTP/1.1" -/- (-%)

```

I've tried the following so far, with no effect:
[LIST]
[*]Disabling Django's GzipMiddleware to see if that helps (it doesn't).
[*]Using ```
SetOutputFilter DEFLATE
   SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png|rar|zip|pdf)$ no-gzip dont-vary
``` instead of the various ```
AddOutputFilterByType
``` statements.
[*]Disabling caching by Apache.
[*]Putting ```
SetOutputFilter DEFLATE
``` in the ```
<LocationMatch "/media/(c|j)/">
```.
[*]Using ```
AddOutputFilter DEFLATE .css .js ...
```
[*]Removing the ```
Header append Vary
``` statements.
[/LIST]

And possibly a few other things. The browser is definitely sending Accept-Encoding: gzip,deflate headers, it just seems that Apache is ignoring them for some reason.

Any help would be much appreciated.

---

