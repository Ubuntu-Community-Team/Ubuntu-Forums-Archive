---
title: "apache help"
date: 2009-10-05
forum: Software
---

### Post by vksingh on 2009-10-05
Hi,

I have installed mediawiki on a server. URL is the following:

[http://wiki.iiitb.ac.in/mediawiki](http://wiki.iiitb.ac.in/mediawiki)

It is using apache2 webserver and platform is ubuntu9.04.

I want to make it such that if I type [http://wiki.iiitb.ac.in](http://wiki.iiitb.ac.in) , it should automatically gets redirected to [http://wiki.iiitb.ac.in/mediawiki](http://wiki.iiitb.ac.in/mediawiki).


Please help.....

:(

---

### Post by HomoGleek on 2009-10-05
Make a file in your public_html called index.php and put this in it.
```

<?php
header("Location: [http://wiki.iiitb.ac.in/mediawiki](http://wiki.iiitb.ac.in/mediawiki)");
?>

```Think thats correct.

Or you could use mod_rewrite?

---

### Post by vksingh on 2009-10-05
Thanks , It worked.

---

### Post by vksingh on 2009-10-05
Can you suggest some websites to learn PHP coding.

---

### Post by guillermolisi on 2009-10-05
> **vksingh said:**
> Can you suggest some websites to learn PHP coding.
Have you visit the[ php website]("http://php.net/") where you'll find an [introductory tutorial]("http://www.php.net/tut.php"), a [manual]("http://www.php.net/docs.php") and [resources links]("http://www.php.net/links.php") ?

---

### Post by vksingh on 2009-10-05
Thanks, Its really helpful..........

---

