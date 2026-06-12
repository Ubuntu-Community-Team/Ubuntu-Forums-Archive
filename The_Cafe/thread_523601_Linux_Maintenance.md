---
title: "Linux Maintenance"
date: 2007-08-12
forum: The Cafe
---

### Post by ShareBuntu on 2007-08-12
Hi,

So I've been using Linux quite enthusiastically for the last 7 months. I started off on Ubuntu but moved onto Fedora to broaden my horizons somewhat.

Now I understand this has been asked numerous times but I'm looking for some maintenance tools besides fsck. Surely there must be tools and/or procedures to check the system's health and clean out garbage.

Any recommendations?

---

### Post by smoker on 2007-08-12
have a look here:
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

### Post by ShareBuntu on 2007-08-12
> **smoker said:**
> have a look here:
[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

Thanks for the reply. Unfortunately most of that applies to Debian based distros and since Fedora is RPM based I can't really use any of that. Are you aware of RPM equivalents?

---

### Post by ssam on 2007-08-12
there a few places where files build up that you may not need.

~/thumbnails stores thumbnails of image files that you have looked with nautilus. I have seen this grow to hundreds of MB. you may have thumbnails for images that you do not have on the computer any more. it is safe to delete as the thumbnails get regenerated when needed.

~/.cache might also hav things you dont need.

/var/log/ you might have lots of old log files

/var/cache/apt can get pretty big.

there are probably a lot of others

i am sure someone was writing a tool that would help cleanup all these things, but i can't find it.

---

