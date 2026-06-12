---
title: "gutsy apt-get error"
date: 2010-06-21
forum: Server Platforms
---

### Post by grcunning on 2010-06-21
I am tasked with backing up our gutsy web server, and then upgrading it to lucid.
to do this I need to back up /var/www, /home, /etc, and mysql.
The problem is that I read a post on how to burn this data to dvd by using dvd+rw-tools,but it requires me to install that package, and I am getting 404 not found errors on all the repositories when doing an apt-get install dvd+rw-tools, or even doing an apt-get update.
The server has no graphical interface, so I can't use k3b or anything like that. is there any way to install this package, and do an apt-get update?
Thanks

---

### Post by snowpine on 2010-06-21
Gutsy reached its "end of life" back in 2008 and the repositories were moved to old-releases. So edit your /etc/apt/sources.list and change all of the URLS from "...archive.ubuntu.com..." to "...old-releases.ubuntu.com..."

That should allow you to install the backup application.

I would recommend a fresh reinstall of 10.04, rather than trying to upgrade from 7.10, but if you really want to try it: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

