---
title: "Website browsing logging"
date: 2014-12-26
forum: Ubuntu, Linux and OS Chat
---

### Post by bghayad on 2014-12-26
Hello;

To be able to know the used method and the corresponding page and script that was used for each field in a website page, I need to have logging method for website browsing. For example, based on the website session, I can know the activities that was done by the user on the website page (based on the session). This will help me to analyze the script and being able to do customization of resolving any bugs. 

How I can obtain this logging tool? How I can enable it?

Regards
Bilal

---

### Post by TheFu on 2014-12-28
The only way is to be a MITM - usually a proxy is the best answer for that and preventing the desktop PC access to the internet without using the proxy is necessary.  Remove the default route and DNS for all traffic to the desktop - only the proxy server should have that access.

BTW - this isn't the correct forum for this question.

If you want something that is desktop only (i,e. without a proxy server), then I suspect setting up logging with IPtables will be the only way - normally browser logs are per-user and inaccessible.

---

