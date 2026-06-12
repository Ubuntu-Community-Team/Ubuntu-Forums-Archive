---
title: "htaccess redirect"
date: 2009-07-24
forum: Server Platforms
---

### Post by divinequran on 2009-07-24
Hi,

i have redirected using the following code.

```
RewriteEngine on
RewriteCond %{REQUEST_URI} ^/(.*).htm
RewriteRule ^(.*).htm http://www.mysite.com/test/test.php?ho=$1 [L]
```

My requirement is to display test.php?ho=hi.htm as hi.htm . it displays properly on my site. but not on my localhost, how do i configure it? in my apache.

---

