---
title: "Recent Update Wants to Remove Google Earth"
date: 2013-08-06
forum: Ubuntu Development Version
---

### Post by OGpmpdog on 2013-08-06
Hello Fam,

It's been awhile...I hope everyone survived the hackfest.

I've been running UG Saucy since April, and I'm SO bored...hardly any breakage, and my dinosaur T61 is running like new!!  Gnome-shell 3.84 Rocks!! (if you have at least 4 GB of RAM:D).

There was a RAM memory leak, but that was fixed weeks ago.

I use GE constantly, and I believe it's one of those "gotta have" applications.

However, per Tim Lunn, lib32 has been eliminated, and the GE packages need to be updated.  GE current version depends HEAVILY on lib 32...

Also, on my laptop, I can use a scroll-bar and see a 7-day weather forecast; but, on my desktop, only a 2-day forecast is viewable...strange!!

---

### Post by JMB74 on 2013-08-07
Not going to work without problem until Google update their packages to reflect those package changes in ubuntu/debian.

As long as the other dependencies are installed (lsb etc), you can work around the problem by making a dummy ia32-libs package using [equivs.]("http://packages.ubuntu.com/saucy/equivs")

Have google earth working on saucy here OK by doing that.

---

