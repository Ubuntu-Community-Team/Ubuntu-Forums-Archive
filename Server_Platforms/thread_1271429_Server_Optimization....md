---
title: "Server Optimization...?"
date: 2009-09-20
forum: Server Platforms
---

### Post by Sarteck on 2009-09-20
Okay, I have just set up a server on Linode with Ubuntu 9.04, Nginx 0.8.15, PHP with PHP-FPM patch, Xcache, and MySQL.  The server is mostly running vBulletin pages.

Occasionally (but increasingly), we get "504" errors, and after much searching, I read that (since they are "upstream" errors) the errors were NOT being caused by Nginx, but most likely by slow queries in MySQL or misconfiguration in PHP.

There are dozens and dozens of pages I've read about optimizing MySQL, and that will be my next target, but I'm having trouble finding any docs for optimization of PHP-FPM.  COuld someone point me to the right direction, please?

---

