---
title: "apache2 - default display of files"
date: 2007-08-27
forum: Server Platforms
---

### Post by rbprogrammer on 2007-08-27
ok, so when i go to any directory before i have an index page setup, i want the default page to be displayed with monospaced text.  preferably courier new.

i have a picture that is what is normally display.. **how do i change some settings so that it will be monospaced??**

---

### Post by a9k on 2007-08-27
The documentation for the module that does directory listing is here:
[http://httpd.apache.org/docs/2.2/mod/mod_autoindex.html]("http://httpd.apache.org/docs/2.2/mod/mod_autoindex.html")

You should be able to do something with 'IndexStyleSheet' directive and your own custom CSS. Or maybe something in the header using the 'HeaderName' directive.

All my Mac browsers use a fixed font for directory listings.

---

### Post by rbprogrammer on 2007-08-27
> **a9k said:**
> 
All my Mac browsers use a fixed font for directory listings.

yup, i have that on my firefox, but for some reason my website would use times new roman or something like that.
> **a9k said:**
> 
The documentation for the module that does directory listing is here:
[http://httpd.apache.org/docs/2.2/mod/mod_autoindex.html](http://httpd.apache.org/docs/2.2/mod/mod_autoindex.html)

You should be able to do something with 'IndexStyleSheet' directive and your own custom CSS. Or maybe something in the header using the 'HeaderName' directive.

i'll check that out later and get back if i have any problems.  i knew there was something in the apache2 docs but i had no idea what to look for.

---

