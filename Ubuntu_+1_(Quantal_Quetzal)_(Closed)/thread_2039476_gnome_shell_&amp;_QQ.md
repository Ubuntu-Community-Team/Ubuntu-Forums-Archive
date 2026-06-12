---
title: "gnome shell &amp; QQ"
date: 2012-08-08
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by sammiev on 2012-08-08
Well I guess today's updates broke gnome shell using gnome. Everything else seems good so far. Time to test a little more. It has been great so far. :)

---

### Post by Harry33 on 2012-08-09
> **sammiev said:**
> Well I guess today's updates broke gnome shell using gnome. Everything else seems good so far. Time to test a little more. It has been great so far. :)

The problem is the new gnome-bluetooth package (v.3.5.5-0ubuntu1).
There was a soname change. Libgnome-bluetooth10 => libgnomebluetooth11.

Here is a corrected gnome-shell built against the new gnome-bluetooth:
[https://launchpad.net/ubuntu/quantal/+source/gnome-shell/3.5.4-0ubuntu2](https://launchpad.net/ubuntu/quantal/+source/gnome-shell/3.5.4-0ubuntu2)

This will very soon hit the QQ repos.

---

### Post by sammiev on 2012-08-09
Hi Harry and thanks like usual. :) I will mark it solved when it hits the repos.

---

