---
title: "Apache directory listing, HELP pls"
date: 2015-12-09
forum: Server Platforms
---

### Post by john493 on 2015-12-09
hello!

I need some help into solving this. Basically what i need to do is enable directory listing for a certain directory sorted alphabetically displaying first 10 characters of the names.

Anyone got a good idea of how to do this??

---

### Post by SeijiSensei on 2015-12-10
You can do it with [Apache]("http://httpd.apache.org/docs/2.2/mod/mod_autoindex.html"), but you'll get the complete file names.  To truncate them to ten characters you need to write a script.

Indexing is disabled by default.  You need to add an "Options Indexes" directive to the <Directory> stanza for the directory you need to list.

The default for directories with indexes enabled is alphabetical.

---

