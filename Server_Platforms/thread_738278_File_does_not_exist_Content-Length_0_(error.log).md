---
title: "File does not exist: Content-Length: 0 (error.log)"
date: 2008-03-28
forum: Server Platforms
---

### Post by breiko on 2008-03-28
[Fri Mar 28 17:11:26 2008] [error] [client 74.6.23.xxx] File does not exist: /home/breiko/public_html/MYDOMAIN.com/php/Content-Length: 0

Hi, I have plenty of these lines on my website error.log.
I can't figure out which file is missing!! Sounds wired..

---

### Post by breiko on 2008-03-30
(up)

---

### Post by breiko on 2008-03-31
Ok, I solved. Maybe someone could be interested so, those ips are yahoo crawlers (slurp) that try to request for non existent pages.

Here what yahoo reported in the website:

[I]Some web servers send a site navigation page or other response page with a "HTTP 200 OK" response instead of a "HTTP 404 Not Found" result for page-not-found conditions. To check on web server handling of page-not-found conditions, Yahoo! Slurp occasionally sends deliberately odd URLs built from random words to sites from which no 404 results have been seen. These URLs are built intentionally to not match any actual content at the site. We save information on the web server response to requests for non-existent pages so we can correctly recognize and remove obsolete URLs in our search database.
A Yahoo! Slurp check for 404 results from a web server consists of requests for up to 10 such URLs. The check for 404 behavior is not a normal part of Yahoo! Slurp site refresh, so such requests are rare.[/I]

---

