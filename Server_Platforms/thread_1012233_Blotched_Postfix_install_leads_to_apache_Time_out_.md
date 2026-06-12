---
title: "Blotched Postfix install leads to apache Time out error"
date: 2008-12-15
forum: Server Platforms
---

### Post by neuromancer2701 on 2008-12-15
I had Wordpress MU up and running on my home Ubuntu(Ibex) box.  I tried installing my own mail server following the directions on [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)  (man that needs to be simplified/shortened)

At some point I realized I messed up the install so I tried uninstalling most of the major components.  All of the LAMP stack is still there.  But now I get a timeout error(internal) when trying to access the website.  I figure it might have something to do with the firewall software(shorewall) but I uninstalled that.  Also when restarting apache2 is refers to itself as 127.0.1.1 which seems odd to me because that is not the standard localhost.

Any hints what could be wrong?

Thanks

---

### Post by neuromancer2701 on 2008-12-15
Fix 1 module of shorewall was still installed

---

