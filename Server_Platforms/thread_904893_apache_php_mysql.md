---
title: "apache php mysql"
date: 2008-08-29
forum: Server Platforms
---

### Post by SpazDes on 2008-08-29
I'm pretty sure I have posted in the wrong section so if I have please move my post. Anyhow I seem to be having problems with getting apache2 to parse php pages properly. I am not sure why, but when it happend I was trying to get PHP to support GD better by following this:

[http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu](http://cumu.li/2008/5/13/recompiling-php5-with-bundled-support-for-gd-on-ubuntu)

Anyhow I have uninstalled apache2/php5/mysql about 20 times if not better, and still to no avail it isn't working... What do I need to try now? I'm asking anyone willing to help, I'll post anything needed to help figure this out, just someone please help me. :(

---

### Post by p_quarles on 2008-08-30
Moved to Server Platforms. 

One thing I'm not completely clear on from your post: is PHP not parsing at all, or is parsing partially/inconsistently? Not "properly" could potentially mean either. :)

---

### Post by cariboo on 2008-08-30
Try:

```
sudo apt-get install php-config
```

That should install some extra dependencies you are missing

Jim

---

### Post by windependence on 2008-08-30
> **SpazDes said:**
> 
Anyhow I have uninstalled apache2/php5/mysql about 20 times if not better, and still to no avail it isn't working... What do I need to try now? I'm asking anyone willing to help, I'll post anything needed to help figure this out, just someone please help me. :(

Do you think after re-installing 2 or 3 times it was pretty obvious this wasn't the fix. Yes, I know, sometimes this works in Windoze, but in the Linux world we try to fix things if we can.

Try Jim's suggestion above, and if that doesn't work, DO NOT RE-INSTALL, get back to us and we will troubleshoot and try to properly fix the problem. When working on an issue like this, it's important that you do one thing at a time, test it and if it doesn't work, back it out and try something else. That way there is no need for re-installing ;)


-Tim

---

### Post by mbeach on 2008-08-30
were you looking for options not available through the php5-gd package?  If not, installing "php5-gd" should give you most functionality.  Which application are you using that requires gd support in php?

---

