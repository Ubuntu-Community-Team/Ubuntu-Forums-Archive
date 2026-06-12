---
title: "What does the FAIL2BAN BadBots block ? Only Authentication related?"
date: 2016-07-01
forum: Security
---

### Post by lexgabrees on 2016-07-01
Hi all,

I  am wondering if fail2ban is used only in order to block IP  addresses that are from which there are authentication failures (SSH /  HTTP auth. etc) or that it is also used for blocking Bots which crawl  the content of 
web pages (normal webpage traffic) ??

  I know there is a BadBots part in the jail.conf file, but is that  only blocking bots that try to break through authentication ? Or can I  block bots from visiting my web pages (and scraping) with this ??


  Thanks, Lex

---

### Post by Habitual on 2016-07-01
Hello, and welcome!

fail2ban can be used for both.
In fact, I only have 2 jails, ssh and a "custom" one that prevents exactly what you are describing.
I started my custom filter from the badbots.conf example and built it from there.
It targets 222 mis-behaving or poorly configured clients that try a whole host of stupid bot tricks.
It includes EOL browsers and OSs and creepy stuff like 
```
w00tw00t
``` or ```
\\x16\\x03\\x01\\x01\\ # asking for https without a browser?
``` #Comment mine.
It includes unsupported releases of Seamonkey, Firefox, MSIEs and Chrome browsers.

There are quite a few jails in fail2ban and those can cover a range of **usual** situations. But the bottom line is,
Why have more than 2? YMMV.
You may need more if you have > 1 service needing basic protection.

ssh in fail2ban 0.8.11-1 starts up right after install.
The scrapy/bot-like behavior can be reduced also, with custom filters, or just one.

If you work for bean counters or otherwise need-to-know by segregation, you can have as many jails as you like.
But I only need ssh and "basic web protection", so I only need 2 jails. ssh and custom.

Tell me about your host. Its environment. Its clients, if any, In general terms.
Its **content** management systems, if any, or all. In general terms.

See my signature link for Sucuri.net

Some things to read/bookmark:
[http://johannburkard.de/blog/www/spam/?page-num=1](http://johannburkard.de/blog/www/spam/?page-num=1)
[http://ubuntuforums.org/showthread.php?t=2305251](http://ubuntuforums.org/showthread.php?t=2305251)

Subscribed with interest...

Edit:
> **lexgabrees said:**
> I know there is a BadBots part in the  jail.conf file, but is that  only blocking bots that try to break  through authentication ?
Define "authentication"...
It _can_ for instance be used to block access to wp-login.php, yes.

---

