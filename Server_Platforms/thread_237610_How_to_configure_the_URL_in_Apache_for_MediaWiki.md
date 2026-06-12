---
title: "How to configure the URL in Apache for MediaWiki?"
date: 2006-08-16
forum: Server Platforms
---

### Post by cocotu on 2006-08-16
Hello friends, here at work we installed wiki in a LAMP server for use in the Intranet. What we want to do is just type the IP address and get the wiki page. Now, we type the IP: 10.0.0.1 and get the folder which is: /mwiki1.7.1. We were trying to configue apache at /var/www/mwiki1.7.1 but I get an error:

Not Found
The requested URL /mwiki1.7.1/index.php/Main_Page was not found on this server.
-----------------------------------------------------------------

Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at 10.0.3.107 Port 80

How can I acomplish this??

Thanks...

---

### Post by UbuWu on 2006-08-27
See here: [http://www.ubuntuforums.org/showthread.php?t=243804](http://www.ubuntuforums.org/showthread.php?t=243804)

---

### Post by cocotu on 2006-08-30
Thanks UbuWu, I have tried this (as you can read in my previous post). We had to place everything at the root of /var/www and eliminate the /wiki directory. This procedure works but it is kind of messy.

Thanks again

---

