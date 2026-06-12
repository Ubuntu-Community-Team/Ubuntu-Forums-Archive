---
title: "default Apache document"
date: 2008-10-20
forum: Server Platforms
---

### Post by Vegan on 2008-10-20
In the Apache config file, the default document is index.html, is it possible to specify multiple types such as index.php in addition to index.html etc. 

This way I can use PHP for a test site and use index.php as the main document. I wanted to leverage PHP since its available to the LAMP setup I am using.

Part of the motivation is for things like ad rotators which are easy enough to conjure up on PHP from a text file or MySQL etc.

By leveraging LAMP I wanted to exploit the tools to maximum advantage.

---

### Post by mbeach on 2008-10-20
edit the DirectoryIndex directive in /etc/apache2/mods-available/dir.conf to list index.php first.

Documentation:
[http://httpd.apache.org/docs/2.0/mod/mod_dir.html](http://httpd.apache.org/docs/2.0/mod/mod_dir.html)

mb.

---

### Post by Vegan on 2008-10-21
Is it OK to override the DirectoryIndex on a per item basis. I have several vhosts in Apache and this would make it more flexible.

This way I can make old sites HTML, others XHTML and other PHP driven as needed.

---

