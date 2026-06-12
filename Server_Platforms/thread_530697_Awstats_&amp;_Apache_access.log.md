---
title: "Awstats &amp; Apache access.log"
date: 2007-08-20
forum: Server Platforms
---

### Post by joegiampaoli on 2007-08-20
Hello, I just installed Awstats and obviously it's reading my /var/log/apache2/access.log file, but what I don't understand, If I remove that current log file and let Apache recreate the new one. Why is Awstats still showing me the older log information, I want to reset that info, Any one? I just keep deleting the recreated file over and over, go to my Awstats page, hit the "Update Now" link in Awstats (enabled in awstats.conf) and nothing, still shows the same old crap....:confused::confused::confused:

---

### Post by Mr. C. on 2007-08-20
In your config file, there is a variable DirData which indicates where awstats keeps *its* data.  Go remove that data.

MrC

---

### Post by joegiampaoli on 2007-08-20
Ah!!!
I knew it was caching all that info somewhere else!

Thx! Worked perfectly fine!

:guitar:

---

