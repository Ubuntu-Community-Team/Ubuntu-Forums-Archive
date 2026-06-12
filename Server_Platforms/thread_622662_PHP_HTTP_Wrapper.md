---
title: "PHP HTTP Wrapper"
date: 2007-11-25
forum: Server Platforms
---

### Post by herbie_popnecker on 2007-11-25
How do I set my php to allow a URL include
```

<?php include_once "http://forum.sitename.com/test.php"; ?>

```
as
```

<?php include_once "/var/www/anothersite/includes/test.php"; ?>

```
does not work properly?
Using a URL gives the error:
```

url file-access is disabled in the server configuration
```

I tried editing et/php5/apache2/php.ini
```
;;;;;;;;;;;;;;;;;;
; Fopen wrappers ;
;;;;;;;;;;;;;;;;;;

; Whether to allow the treatment of URLs (like http:// or ftp://) as files.
allow_url_fopen = On

; Whether to allow include/require to open URLs (like http:// or ftp://) as files.
;allow_url_include = Off
;;; changed to this
allow_url_include = On

```
but that didn't do anything

---

### Post by herbie_popnecker on 2007-11-25
Q#2 about PHP
what's the difference between
   <?php include_once
and
   <?php include

??

---

