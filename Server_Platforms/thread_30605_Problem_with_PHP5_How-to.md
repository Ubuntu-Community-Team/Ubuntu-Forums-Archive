---
title: "Problem with PHP5 How-to"
date: 2005-04-29
forum: Server Platforms
---

### Post by RyaninZion on 2005-04-29
I have been following the [PHP5 from source](http://www.ubuntulinux.org/wiki/PHP5FromSource)  tutorial over at the Ubuntu Wiki, but am unable to complete the process.

The configuration is aborting when it hits this line:

```
--with-apxs2=/usr/bin/apxs2 \
``` 

I did a search of my file system and found that I do not have a file or directory named apxs2 (or apxs) on my computer.  I do have Apache 2 and PHP 4 installed, and they are working.

Any ideas?

---

### Post by defkewl on 2005-04-29
Did you install apache2 from source or with apt-get?

If from source, where is it located? 
Probably it would be located in /usr/local/apache2
if it is, then it should've been like this: --with-apxs2=/usr/local/apache2/bin/apxs2 \

---

### Post by RyaninZion on 2005-04-29
I installed Apache2 with apt-get.  

I have done a search of my file system, and I have no file named apxs2 anywhere on my computer.

When installed via apt-get, does Apache install in a different way?

---

