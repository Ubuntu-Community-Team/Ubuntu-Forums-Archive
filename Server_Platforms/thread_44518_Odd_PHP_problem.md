---
title: "Odd PHP problem"
date: 2005-06-26
forum: Server Platforms
---

### Post by BenjyD on 2005-06-26
I upgraded my server from Warty to Hoary today and am having an odd problem with Apache2 and PHP.

PHP scripts are executed correctly if they are accessed directly (as [http://example.com/test.php](http://example.com/test.php), for example). But if I try to access them indirectly (by visiting [http://example.com/](http://example.com/) with an index.php file in the DocumentRoot), the PHP source code is served without being executed.

I've tried a complete apt-get remove --purge of apache2 and php, so I'm using the default configuration AFAICS. I've enabled all the PHP modules with a2enmod and added the index.php to DirectoryIndex.

Does anyone know what the problem is?

---

### Post by LordHunter317 on 2005-06-26
Are you running any other modules, like mod_rewrite?

---

### Post by deuce868 on 2005-06-26
is .php in your apache config as a valid directory index extension?

Check DirectoryIndex index.php in your /etc/apache2/apache2.conf

---

### Post by BenjyD on 2005-06-27
Thanks, I found the mistake: I had the DirectoryIndex index.php directive in the main configuration but not the virtual host's configuration. It all works fine now.

That makes precisely one problem for a complete upgrade from Warty to Hoary. Not bad!

---

