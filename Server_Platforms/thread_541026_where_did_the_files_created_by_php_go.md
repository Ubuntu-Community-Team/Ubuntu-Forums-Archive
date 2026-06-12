---
title: "where did the files created by php go?"
date: 2007-09-02
forum: Server Platforms
---

### Post by tweston on 2007-09-02
am running Ubuntu 7.04, Apache 2, PHP 5.2.1

I have a PHP script which creates a subdirectory in the document root directory using the PHP function mkdir. It then calls a PERL script that writes several files into this subdirectory. The subdirectory and the files have owner:group www-data:www-data

My problem is this: after about a day, the subdirectory and all the files therein are gone! How? Why? Can/should I prevent this?

---

