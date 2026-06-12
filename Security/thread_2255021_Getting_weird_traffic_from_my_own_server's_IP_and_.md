---
title: "Getting weird traffic from my own server's IP and external IP as well"
date: 2014-12-01
forum: Security
---

### Post by carbonzee on 2014-12-01
```
107.170.31.34 - - [01/Dec/2014:22:37:18 +0200] "GET /js/jordan24/6145_jordan.html?alt_ts=ts HTTP/1.0" 500 610 "-" "-"
157.55.39.180 - - [01/Dec/2014:22:37:18 +0200] "GET /js/jordan24/6145_jordan.html HTTP/1.1" 200 309 "-" "Mozilla/5.0 (compatible; bingbot/2.0; +http://www.bing.com/bingbot.htm)"
107.170.31.34 - - [01/Dec/2014:22:37:18 +0200] "GET /js/jordan24/6145_jordan.html?alt_ts=ts HTTP/1.0" 500 610 "-" "-"
107.170.31.34 - - [01/Dec/2014:22:37:19 +0200] "GET /css/longchamp24/5768_longchamp.html?alt_ts=ts HTTP/1.0" 500 610 "-" "-"
157.55.39.180 - - [01/Dec/2014:22:37:18 +0200] "GET /css/longchamp24/5768_longchamp.html HTTP/1.1" 200 308 "-" "Mozilla/5.0 (compatible; bingbot/2.0; +http://www.bing.com/bingbot.htm)"
107.170.31.34 - - [01/Dec/2014:22:37:19 +0200] "GET /css/longchamp24/5768_longchamp.html?alt_ts=ts HTTP/1.0" 500 610 "-" "-"
107.170.31.34 - - [01/Dec/2014:22:37:19 +0200] "GET /css/longchamp24/12106_longchamp.html?alt_ts=ts HTTP/1.0" 500 610 "-" "-"
157.55.39.94 - - [01/Dec/2014:22:35:18 +0200] "GET /css/longchamp24/12106_longchamp.html HTTP/1.1" 200 0 "-" "Mozilla/5.0 (compatible; bingbot/2.0; +http://www.bing.com/bingbot.htm)"
107.170.31.34 - - [01/Dec/2014:22:37:25 +0200] "GET /js/jordan24/9788_jordan.html?alt_ts=ts HTTP/1.0" 500 610 "-" "-"
157.55.39.175 - - [01/Dec/2014:22:37:24 +0200] "GET /js/jordan24/9788_jordan.html HTTP/1.1" 200 309 "-" "Mozilla/5.0 (compatible; bingbot/2.0; +http://www.bing.com/bingbot.htm)"
107.170.31.34 - - [01/Dec/2014:22:37:25 +0200] "GET /js/jordan24/9788_jordan.html?alt_ts=ts HTTP/1.0" 500 610 "-" "-"

```
I deleted these files as they seemed to be some files I couldn't figure out how they entered into my wordpress installation's folder, but these entries won't stop showing in my logs, I tried multiple security tools like rkhunter and chkrootkit but couldn't find anything.

How can I diagnose this further? It is causing my server to become unresponsive.

---

### Post by bashiergui on 2014-12-01
Is 107.170.31.34 your IP and mgc-gas . com your site?

Take it offline until you can figure out what's up with it. Look at all the logs. Look for users logging in when you know they shouldn't have. Check if php files have been modified. Look at any modified php files in an editor to see what they changed.

---

### Post by carbonzee on 2014-12-01
Yes, that's correct. I've noticed that any ?alt_ts=ts URLs on my site redirect to cheapugg.ru, which makes me think wordpress has been hijacked with that query string. Any ideas of where to look?

---

### Post by carbonzee on 2014-12-01
Check this, the first result leads to the hijacker website.

[https://www.google.jo/search?q=alt_ts%3Dts&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=firefox-aurora&channel=fflb&gfe_rd=cr&ei=DRd9VIKgCaWs8we41IKYDQ#rls=org.mozilla:en-US:unofficial&channel=fflb&q=alt_ts%3Dts+protection](https://www.google.jo/search?q=alt_ts%3Dts&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=firefox-aurora&channel=fflb&gfe_rd=cr&ei=DRd9VIKgCaWs8we41IKYDQ#rls=org.mozilla:en-US:unofficial&channel=fflb&q=alt_ts%3Dts+protection)

---

### Post by carbonzee on 2014-12-01
I just updated wordpress and the redirect no longer works.

---

### Post by carbonzee on 2014-12-01
CPU still maxed out due to those threads that keep opening up according to apachectl fullstatus. What can I do next?

---

### Post by bashiergui on 2014-12-01
Reimage. Restore from backups.

Sorry, that sucks :-/

---

### Post by carbonzee on 2014-12-01
Resolved it by adding a RewriteCond against that query string as per  this guide because using iptables to ban IP addresses was too hectic as  they were too many different IPs. Thought I'd share it for future  reference if anyone comes across the same scenario.

[http://perishablepress.com/eight-ways-to-blacklist-with-apaches-mod_rewrite/](http://perishablepress.com/eight-ways-to-blacklist-with-apaches-mod_rewrite/)

---

### Post by carbonzee on 2014-12-01
Thank you bashiergui, appreciate your input here.

---

### Post by bashiergui on 2014-12-05
Did you install any pirated plugins? If you got one that's backdoored the problem will persist.

---

### Post by carbonzee on 2014-12-07
I actually disabled all WordPress plugins one by one to try and find if there were any causing the problem, but the problem persisted. There were some strange folders created in the Wordpress folder, I wonder how those may have been created, any idea if its possible to find out what or who created those?

Anyways, I think I need to learn more about hardening security on my VPS's.

---

