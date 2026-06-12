---
title: "apache mod_rewrite"
date: 2010-01-28
forum: Server Platforms
---

### Post by cucuru on 2010-01-28
hello! I'm trying to enable the rewrite module in apache, to enabled the module I followed the last entry in the fist page this thread:

[http://ubuntuforums.org/showthread.php?t=7304](http://ubuntuforums.org/showthread.php?t=7304)

When I restart the apache all works fine, so I supose it's enabled

Now I create .htaccess in my apache folder (/home/user/apache), and I write this:

```

RewriteEngine On
RewriteRule ^link([^/]*).html$ test.php?link=$1 [L]

```

And I try to execute this: ./.htaccess, I have this mistakes:

```

./.htaccess: 1: RewriteEngine: not found
./.htaccess: 2: Syntax error: "(" unexpected
```

What are I doing wrong? Thanks!!!

---

### Post by cucuru on 2010-01-28
I found my mistake, I supossed that I had to execute .htaccess, but I hadn't

Thank you anyway! Regards

---

