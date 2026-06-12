---
title: "Cookie Problems with apache and php"
date: 2007-08-22
forum: Server Platforms
---

### Post by offramp13 on 2007-08-22
I have apache, php, and mysql all running on my desktop just fine, except for one thing. I cannot set cookies in a php script. It gives me an error message similar too
```
Warning: Cannot modify header information - headers already sent by (output started at /var/www/sarah/header.php:7) in /var/www/sarah/login.php on line 41
```
I was wondering if there was a way to fix this.

---

### Post by primski on 2007-08-22
well, you get this error when u try to change page's headers, but have already set some output on it.

header(""); function needs to be called before any other output to the page, including all print ""; echo "", and whatever makes an output.

---

