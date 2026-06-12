---
title: "Please help with apache mod_rewrite"
date: 2007-06-04
forum: Server Platforms
---

### Post by an.echte.trilingue on 2007-06-04
I am building a website with lots of dynamic content.  I would like to make user-friendly URLs, much like you see on the [Ubuntu Wiki]("https://help.ubuntu.com/6.10/"), so that instead of seeing [http://www.mydomain.com/page.php?lots_of_variables](http://www.mydomain.com/page.php?lots_of_variables), the user sees [http://www.mydomain.com/page/](http://www.mydomain.com/page/).  I am having real trouble getting apache (version 2.2) to do this transparently.  I can get apache to automatically redirect with this rule:

```
 RewriteRule ^/page/$ http://www.mydomain.com/page.php?lots_of_variables
```

But I would like the process to be transparent to the user.   As far as I can tell you do this with the pass through flag, like this:

```
 RewriteRule ^/page/$ http://www.mydomain.com/page.php?lots_of_variables [PT]
```

However, that gives me an Error 400 Bad Request.

What am I doing wrong?

Thank you,
-mat

---

### Post by jtc on 2007-06-05
If you don't want to do an actual Redirect you shouldn't use a full [http://.](http://.).. adress in the destination. Instead you simply rewrite the incoming request to the file which is to handle it.

```
RewriteRule ^page/?$       page.php?lots_of_variables
```

The question mark I added makes the trailing slash optional.

Please note that different kinds of rewrites belongs on different places in your apache configuration. This kind fits well within <Directory ....> </Directory>

Also note that if we do these kinds of rewrite anywhere else then in the DocumentRoot you might want to use the RewriteBase directive.

---

### Post by an.echte.trilingue on 2007-06-05
Thank you _so_ _very_ _ much_ jtc.  It works.  I spent 6 hours on that yesterday.

Thank you.

---

