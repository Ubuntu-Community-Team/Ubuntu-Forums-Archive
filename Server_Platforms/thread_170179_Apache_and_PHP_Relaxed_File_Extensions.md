---
title: "Apache and PHP: Relaxed File Extensions"
date: 2006-05-04
forum: Server Platforms
---

### Post by charlie. on 2006-05-04
I have written my company's intranet in PHP. To me, it is logical that a request without a file extension be sent to a PHP file with the same name. On windows, I use the following RewriteRule (mod_rewrite) to achieve this:

```
RewriteRule ^(\w+)$ /$1.php [L,QSA]
```

On ubuntu, this behaviour appears to be the default. Is this true?

Consider a site with only one file: test.php. On windows, if I browse to [http://localhost/test](http://localhost/test), I get a 404 error unless I use the rewrite rule above. On linux, I do not - I get test.php even without the rewrite rule.

Thanks for any information.

---

