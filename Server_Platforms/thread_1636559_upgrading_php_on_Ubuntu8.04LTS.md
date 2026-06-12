---
title: "upgrading php on Ubuntu8.04LTS"
date: 2010-12-03
forum: Server Platforms
---

### Post by chrislynch8 on 2010-12-03
Hi,

How can I get an updated version of PHP on Ubunut8.04LTS? I think the version that is on it by default is php5.2.1 - I need to use 5.2.10 at least for a web based application I use.

Is there a way to tell Ubuntu to use this version - I don't what to go to 10.04LTS as that has php5.3 I think.

If I manually install php5.2.10 it might get messy and will Ubunutu damage it when I run an apt-get update?

Rgds
Chris

---

### Post by bsntech on 2010-12-04
I'm not sure if this would help you at all, but I recently added a second version of PHP on my 10.04 server - so I have PHP 5.2.14 running in fast-cgi mode and PHP 5.3.2 running as the apache module.

You can read here how I have both running.  A little bit of changing to my how-to will be needed - but it would be possible.

[http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/1681-install-two-versions-of-php-on-ubuntu-lucid-1004-php-53-and-php-52.html]("http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/1681-install-two-versions-of-php-on-ubuntu-lucid-1004-php-53-and-php-52.html")

---

