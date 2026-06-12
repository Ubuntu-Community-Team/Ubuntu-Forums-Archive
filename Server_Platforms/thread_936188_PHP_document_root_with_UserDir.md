---
title: "PHP document_root with UserDir"
date: 2008-10-02
forum: Server Platforms
---

### Post by PaulusEm on 2008-10-02
I'm wondering if it is possible to set the PHP document_root to the UserDir HTTP folder.
I've enabled the UserDir module, and when I create a index.php file in /home/test/public_html it execs the file when I go to [http://myip/~test](http://myip/~test).
The problem is, when I paste the following in my index.php:

```
<?php

echo $_SERVER['document_root'];

?>
```

It echoes: /var/www

Is it possible to set the document_root to the user's public html folder?

---

### Post by DarwinSurvivor on 2009-04-17
Bump.

I'm also looking for a solution to this problem.

---

### Post by Bachstelze on 2009-04-17
It works fine here, I guess we'll need to see your Apache error logs.

---

### Post by DarwinSurvivor on 2009-04-17
There is no error, so there would be no error log. I simply wanted to know if there was a sanctioned way to find the base directory of the "userdir" folder (ex: /home/user/public_html).


I ended up making a function that does the following
[PHP]ereg('(.*)script_file\.php', $_SERVER['SCRIPT_FILENAME'], $docroot);
return $docroot[/PHP]

---

