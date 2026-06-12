---
title: "awstats stats page"
date: 2006-08-08
forum: Server Platforms
---

### Post by hogman23 on 2006-08-08
Is there any way to make my main awstats page display from a different URL than [http://www.domainname.com/awstats/awstats.pl?config=www.domainname.com](http://www.domainname.com/awstats/awstats.pl?config=www.domainname.com) ?

I would like to link to it like this instead:

[http://www.domainname.com/stats](http://www.domainname.com/stats)

---

### Post by XplOzIOn on 2006-08-09
How about symlink? Have you ever installed phpmyadmin? notice the folder is a symlink. Just make a symlink or rename folder or anything?
just make sure to have that stat site in /va/www/stats/
that would work right away if www root is /var/www and there are no other fancy stuff like symlinks already set there. If this doesnt work give more details about where is the stats site at the moment the acutal folder path.

---

