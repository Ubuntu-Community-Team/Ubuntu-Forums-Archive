---
title: "xhtml and apache2 on ubuntu"
date: 2007-09-27
forum: Server Platforms
---

### Post by ratbastard on 2007-09-27
Umm? 

How do I get my index.xhtml page to work on lamp 606 


I want my home page to be index.xhtml 

I cant seem to find out how to do this?

---

### Post by tr333 on 2007-09-27
Easy way:  change index.xhtml to index.html.  Why bother with the xhtml extension?  It is more likely to screw up in Internet Explorer.  XHTML seems to work fine for me with a .html extension.


Hard way:  set the DirectoryIndex to index.xhtml
[http://httpd.apache.org/docs/2.2/mod/mod_dir.html#directoryindex](http://httpd.apache.org/docs/2.2/mod/mod_dir.html#directoryindex)

---

