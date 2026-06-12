---
title: "Bandwidth statistics per folder/url for a mirror"
date: 2016-07-29
forum: Server Platforms
---

### Post by dudumomo on 2016-07-29
Hi there,

I'm running a small mirror (mirror.freedif.org) and I'd like to monitor and record the statistics of each folder (Or URL) to get some statistics in term of bandwidth.
I don't know which soft I should use to do it.
Ideally, I'd like to get the monthly bandwidth consumption of each folder.

Any suggestion?

Thank you

---

### Post by Graham_Willis on 2016-07-30
1. You can do it for free because all bandwidth-related data is in Apache logs (and if they aren't, then you can configure Apache so they'd be), so it's just a matter of properly summing it up.
2. [http://www.webalizer.org/](http://www.webalizer.org/) if you need some extensive statistics and a nice visualisation.

---

### Post by dudumomo on 2016-10-04
Well, let me reply to my own post.

I'm using GoAccess to do it now:
[http://freedif.org/goaccess-bandwidth-s](http://freedif.org/goaccess-bandwidth-s) ... rtualhost/

And the result is as following:
[http://mirror.freedif.org/Stats/Antergos.html](http://mirror.freedif.org/Stats/Antergos.html)

Hope it can help others.

---

