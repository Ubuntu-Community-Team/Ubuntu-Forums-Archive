---
title: "DokuWiki caused SegFault in Apache/mod_php"
date: 2005-03-18
forum: Server Platforms
---

### Post by goofrider on 2005-03-18
I'm rather lost about how to fix this. I tried to install DokuWiki, which only involves copying the PHP files to ~/public_html. But everytime I tried to view the page in a browser nothing happens, Apache's error log says the child process terminated due to a segmentation fault. I'm using mod_php BTW.

I also try to interprete the page using php-cli in a shell, also nothing happens. PHP does not provide any error log out regardless of loglevel, so I'm assuming PHP segfault before it has a chance to output to log.

How can I troubleshoot this?

---

### Post by akaihola on 2006-01-02
I had a similar problem with both mod_php and mod_python installed and trying to access mysql databases. See:
[http://www.modpython.org/pipermail/mod_python/2004-January/014886.html](http://www.modpython.org/pipermail/mod_python/2004-January/014886.html)

---

