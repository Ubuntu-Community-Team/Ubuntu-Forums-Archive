---
title: "Edubuntu - proxy server filtering?"
date: 2012-08-29
forum: Server Platforms
---

### Post by Sternfan on 2012-08-29
Hi all,
I have an XP lab that I would like to switch out to Edubuntu.  One of the things I need to know that works is using Squid for caching and filtering websites.

Currently I can look in the squid logs and see the websites LAB01 (for instance) visited.

If I switch to Edubuntu, will the log still reflect this?  Or, since everything "sits" on the Edubuntu server, will the log only have all the websites, but coming from the server itself?

I am concerned that if I switch to Edubuntu, that some student will logon to LAB01 - visit an inappropriate website - but the logs will only show the edubuntu server... 

For purposes of this example, the squid box is a separate server.

Any info greatly appreciated.

Rob

---

### Post by Sternfan on 2012-09-01
bump - anybody?

---

### Post by dcrst75 on 2012-09-04
I do not understand exactly what you want but, if you use squid proxy, all access through it is reflected on access.log with date, time, IP, url...

---

