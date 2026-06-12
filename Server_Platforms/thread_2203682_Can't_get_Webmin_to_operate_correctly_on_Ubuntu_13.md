---
title: "Can't get Webmin to operate correctly on Ubuntu 13.10"
date: 2014-02-04
forum: Server Platforms
---

### Post by makdaddydavisjr on 2014-02-04
I'm fairly novice to Ubuntu in general, and have used it multiple times in the past, but primarily just for tinkering around. I've done quite a bit of windows server work, but I've never actually set one up in Ubuntu, so I'm fairly spoiled by IIS and its easy to use GUI.

I managed to Apache, MySQL, PHP, and webmin installed on 13.10, but while trying to configure Apache through webmin, I've run into a strange issue.

I'm trying to use webmin to modify the port apache uses for outside communication (from 80 to say 8700), but when I go to Apache>Global Configuration>Networking and Addresses the option isn't listed as I've seen in some screen shots. In fact, the only options that are listed for my to modify are "Multiple requests per conneciton" "Request timeout" and "Keep-alive timeout". 

Does anyone have any idea what is going on?

---

### Post by volkswagner on 2014-02-05
Although Webmin states it's compatible with Ubuntu, you will run into issues.  Ubuntu does not support Webmin.

You may have better luck with an earlier version of Ubuntu such as 12.04.

You would be better off choosing a distro with better support for Webmin, or drop Webmin in favor of directly editing necessary config files.

Here are some valuable links from the sticky at the top of this server forum.

[https://help.ubuntu.com/10.04/serverguide/index.html](https://help.ubuntu.com/10.04/serverguide/index.html)
[https://help.ubuntu.com/10.04/serverguide/httpd.html](https://help.ubuntu.com/10.04/serverguide/httpd.html)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

