---
title: "Forbidden access to site"
date: 2018-08-22
forum: Server Platforms
---

### Post by linfan on 2018-08-22
All of the sudden I cannot access my site running Apache 2.4 on Ubuntu 17.10.

An AH01630 error appears in /var/log/apache2/error.log which points to /var/www being the problem, but I deleted that folder by mistake and Apache is still throwing it up as the problem in the error log even though the folders no longer exist.

I noticed in apache2.conf there was:

Include /phpmyadmin/Apache.conf

I tried changing that dir to where my site resides on my box but it didn’t make a difference. The apache file in PhpMyAdmin doesn’t have any path relating to the above. I also added the Require All Granted line but that didn’t make a difference either.

It’s like there is another conf file with the above path but I cannot find it!

---

### Post by wyliecoyoteuk on 2018-08-22
check /etc/apache2/sites-available/000-default.conf

---

### Post by darkod on 2018-08-22
You deleted which folder by mistake, /var/www? That is where apache guards the website files by default.

If the website files are not there any more, where are they? You have to have files in order to serve a website. It's not just getting rid of the error message, you understand that, no?

The config file in /etc/apache2/sites-available has to point to the path where the files are. Otherwise it has no content to offer.

---

