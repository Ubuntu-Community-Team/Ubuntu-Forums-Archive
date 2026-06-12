---
title: "Htaccess and Mod_rewrite"
date: 2005-11-21
forum: Server Platforms
---

### Post by fnando on 2005-11-21
I want to know if is possible to load rewrite rules from a htaccess file. Something like Ubuntu does with modules.

I want to do something like the following:

```

#this file is .htaccess

RewriteEngine On
Load rewrite.rules

```

rewrite.rules is the file with all rules, something like:

```

#this file is rewrite.rules

RewriteRule ^section1/?$ /index.php?area=section1

```

If is possible, how to do it?

Thanks!

---

