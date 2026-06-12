---
title: "Apache Proxy with Virtualbox, perl, and a lot of other nonsense"
date: 2012-01-02
forum: Server Platforms
---

### Post by TTGRULES on 2012-01-02
Ok, so I have an old site (complete legacy code) that runs on windows server 2003... I got fed up dealing with hardware replacements every time it broke so I put it in a virtualbox on a new(er) ubuntu 10.04 server. (YAY!) Anyways, I was trying to configure the apache Mod_Proxy proxypass modules to re-rout any traffic for the specific site to the virtualbox. It worked fine, except none of the perl scripts function right. They all download the html output instead of displaying it... It doesn't happen unless it is going through the reverse proxy server. Any ideas?

~TTGRULES

---

### Post by TTGRULES on 2012-01-02
Figured out what it was... If anyone has the same problem, check perlis.dll on the server 2003 comp... It wasn't outputting the headers right at all... change the script map to perl.exe "%s" %s and it works fine... make sure you print the content-type header

---

