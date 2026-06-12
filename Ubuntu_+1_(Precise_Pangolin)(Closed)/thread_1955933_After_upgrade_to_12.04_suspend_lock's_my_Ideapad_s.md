---
title: "After upgrade to 12.04 suspend lock's my Ideapad s205."
date: 2012-04-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by moteprime on 2012-04-10
I installed 12.04 over the weekend, upgrade didn't work so I made a clean install.
But suspend does not work, I have to unplug it and remove the battery to get it back to life.
With 11.10 I had this problem before, depending on the version of AMD's Catalyst center, but in Precise it also locks up in suspend when using the built in Radeon driver.
What to do, and how do i trouble shot it?
Thanks

---

### Post by s.fox on 2012-04-11
Thread moved to [Ubuntu +1 (Precise Pangolin)]("http://ubuntuforums.org/forumdisplay.php?f=412")

---

### Post by Lazy123 on 2012-04-11
You might have experienced the same bug that I have seen: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/977135](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/977135)

As a workaround you could try installing an older kernel. This one works for me: [http://packages.ubuntu.com/oneiric/linux-image-3.0.0-17-generic](http://packages.ubuntu.com/oneiric/linux-image-3.0.0-17-generic)

---

### Post by moteprime on 2012-04-13
@Lazy123

Thanks. But I never see anything else than a black black screen, no cursor, -nothing.

---

### Post by moteprime on 2012-04-21
I opened a bug report on it:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985528]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/985528")

---

