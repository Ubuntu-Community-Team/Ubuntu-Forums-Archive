---
title: "mail server using database?"
date: 2008-01-29
forum: Server Platforms
---

### Post by incgnito on 2008-01-29
Some time back when I used to use Gentoo their forums used to have a guide on how to setup postfix with virtual users/domains to use a MySQL database for mail storage.  I can't seem to find it here, but I was wondering if anyone here has seen something similar for Ubuntu.  Any help would be appreciated.

Kris

---

### Post by HermanAB on 2008-01-29
There are generic guides for that on the Postfix web site.

Bear in mind though that the only data saved in the database is the user data.  The actual email is still saved in mbox or maildir files, which can be very wasteful of disk space.

If you wish to save everything in a database, so that there will be only one saved copy of any multiple addressed email, then you need Citadel, which uses BerkeleyDB for that.

---

### Post by mmichalik on 2008-01-29
We used this guide for Postfix and it worked really well!

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

But, I have to say, Citadel is pretty awesome looking.  It's GREAT to know that it's out there as an option.

---

### Post by DDuong on 2008-01-29
I believe this is the guide for you?

[http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10)

---

