---
title: "Running production web server with ubuntu on VPS - any suggestions?"
date: 2007-02-28
forum: Server Platforms
---

### Post by mikestefff on 2007-02-28
Hi,

I am nearing the end of design and implementation of my website that I am running on a VPS w/ ubuntu. Everything is setup and running perfectly, as of now, and I wanted to know if there is anything extra I can or should be doing. The site is almost done and will be going live shortly.

Basically, I have never ran a production website and server before. I have a decent amount of linux experience and definitely know what I am doing but I know theres alot of I need to learn. I am asking if anyone could suggest any things I can install or do to ensure everything runs smoothly - anything from security issues, monitoring software, tweaks for performance, protection from bots, certain logs to monitor, database optimization, anything at all that I should know or learn about in order to run this server perfectly.

Currently running on the system:
apache2 (w/ drupal)
php5
mysql
webmin
awstats
postfix
spamassassin
clamav
ssh (for file transferring also - no ftp)

Thank you.
Mike

---

### Post by Sherman.Boyd on 2007-03-09
I would suggest running modsecurity for apache:

[http://www.modsecurity.org/](http://www.modsecurity.org/)

---

