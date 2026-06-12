---
title: "can web admins block wget?"
date: 2010-02-02
forum: The Cafe
---

### Post by sp0tz on 2010-02-02
I was on reddit.com and noticed someone pointing out that a certain website has hidden some easter eggs. There are a bunch of groundhogs hidden all over the site, and if you find and click one, it points you towards a page that gives you a coupon code that you enter during checkout.

I noticed, however, that clicking any groundhog redirects you to the same subdirectory in the website. For example, one will lead you to
[www.foo.bar/whatever/groundhogs/randomcouponname.html](www.foo.bar/whatever/groundhogs/randomcouponname.html)
and another will lead you to
[www.foo.bar/whatever/groundhogs/anothercouponname.html](www.foo.bar/whatever/groundhogs/anothercouponname.html)

Thinking I was super-clever, I figured I would run 
wget [www.foo.bar/whatever/groundhogs/](www.foo.bar/whatever/groundhogs/)
from the terminal and see all the coupon codes. I kept getting 404 errors. Even after finding a couple of devious tricks like the -U option to specify a user agent, I kept getting errors, check it out:


[email]tails@tornado:~/noreason/www.foo.bar[/email]$ wget --wait=20 --limit-rate=20K -r -p -U Mozilla [http://store.foo.bar/photos/](http://store.foo.bar/photos/)
--2010-02-02 21:10:00--  [http://store.foo.bar/photos/](http://store.foo.bar/photos/)
Resolving store.foo.bar... 63.147.61.104
Connecting to store.foo.bar|63.147.61.104|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://www.foo.bar/notfound](http://www.foo.bar/notfound) [following]
--2010-02-02 21:10:20--  [http://www.foo.bar/notfound](http://www.foo.bar/notfound)
Resolving [www.foo.bar](www.foo.bar)... 204.10.64.139
Connecting to [www.foo.bar|204.10.64.139|:80](www.foo.bar|204.10.64.139|:80)... connected.
HTTP request sent, awaiting response... 404 Not Found
2010-02-02 21:10:20 ERROR 404: Not Found.


It seems like the website notices that I'm trying to wget and redirects me to a phony IP that holds no info. Is this possible, or am I using the command wrong? Note that I'm not trying to do anything malicious; I'm definitely not in the market for what these people are selling, I was just wondering at first if wget was the solution to this problem and then why it isn't....


edit: the command seems to do fine without the -U Mozilla option. Wierd. Anyways I'll delete this post or mark it solved it the wobsite finishes downloading as intended.

---

