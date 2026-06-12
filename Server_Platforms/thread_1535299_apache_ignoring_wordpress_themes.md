---
title: "apache ignoring wordpress themes?"
date: 2010-07-20
forum: Server Platforms
---

### Post by hellarough on 2010-07-20
I recently installed wordpress on my server to host from home but when someone visits my blog all they see is generic formatting like in the pictures below (themes are not showing at all). However when I access it from within my network I see the full blog like I am supposed to. 

current set-up:
apache sites-enabled - default (/var/www)
blog - /var/www/blog


contents of /var/www/index.php
```
<? header('Location: /blog/index.php'); ?>
```

I tried just changing the default site to have the doc root at /var/www/blog but then themes did not work at all (internally or externally). I think it is just an apache config issue but I have no clue what I am missing.

---

