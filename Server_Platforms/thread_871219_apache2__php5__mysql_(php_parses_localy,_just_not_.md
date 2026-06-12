---
title: "apache2 : php5 : mysql (php parses localy, just not when requestd from the web)"
date: 2008-07-26
forum: Server Platforms
---

### Post by ferrellw on 2008-07-26
I have a server setup with ubuntu 8.04 as a webhost for [http://networkninja.us](http://networkninja.us). The problem is that the php parses locally, ex 127.0.0.1, or within my lan, but when someone else on the internet requests my pages , the area where the php should be is blank. I have reinstalled everything a few time and cant seem to figure out what the problem is.If requested i will post my conf files, i just didn't want to do that on my first post and overwhelm everyone.

Thanks,
Wesley

---

### Post by windependence on 2008-07-26
Are you excercising your hardware by re-installing a few times? Obviously that is not the problem. Why people insist on doing this is beyond me.

Is your php module loaded in apache? It is really strange that it would work internally but not externally on the same apache server. You may want to check the paths in your php files.

-Tim

---

### Post by cariboo on 2008-07-26
You also may want to check your file ownership and permissions. I would suggest using the same user as your apache user and file permissions should be 755. This is basic info I know but it is always a good idea to check and make sure.

Jim

---

