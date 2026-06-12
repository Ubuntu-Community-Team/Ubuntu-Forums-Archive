---
title: "Apache, PHP5 Segmentation Fault (11), mpm-prefork"
date: 2009-03-29
forum: Server Platforms
---

### Post by chez17 on 2009-03-29
Hello all, I am having a problem with an import script I'm coding. I am very new to server admin so some of my assumptions my be wrong but here is what I think I know. The import script is causing a segmentation fault, I think it is most likely a php5 issue. From what it seems, if I installed the mpm-prefork module, it may solve my problem. But here is my issue. My system says it is installed but I can't see how to get apache to use it. Even the phpinfo() function mentions it in the "Loaded Modules" section, but when I check the /etc/apche2/mods-enabled section, I can't find anything about it. Same for some other mods, it seems apache is loading them but I have no idea from where. I can't seem to figure this one out. Any help is most appreciated.

Also, a lot of sites are telling me to look at "httpd -V" but when I type that in I get "httpd: command not found". Is there a different command for ubuntu?

---

