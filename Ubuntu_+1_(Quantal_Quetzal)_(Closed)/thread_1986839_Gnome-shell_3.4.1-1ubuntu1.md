---
title: "Gnome-shell 3.4.1-1ubuntu1"
date: 2012-05-25
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Harry33 on 2012-05-25
A new gnome-shell has landed on Quantal repos.
Some dependencies have been refreshed, like newer evolution data server.

But, dependency on gir1-2-gjsdbus-1.0 is dropped.
However, do not remove that package, as gnome-shell will not start without it.
That dependency ought to be corrected.

---

### Post by Harry33 on 2012-05-25
Well well, and now trying to install new gjs and libgjs0c would remove gnome-shell along with gir1.2-gjsdbus-1.0.

Haven't figured out why, though.

---

### Post by Harry33 on 2012-05-25
> **Harry33 said:**
> Well well, and now trying to install new gjs and libgjs0c would remove gnome-shell along with gir1.2-gjsdbus-1.0.

Haven't figured out why, though.

Hmm, I figured it out.

Gnome-shell_3.4.1_1ubuntu1 depends on *libgjs0-* (a virtual package)
and the previous libgjs0c_1.32.0-1ubuntu1 provides that.
However, the new libgjs0c_1.32.0-2ubuntu1 does not provide it.

We still need even newer gnome-shell package to get it right.

---

### Post by jbicha on 2012-05-25
Thanks Harry. I need to see if gnome-shell will build on ARM first before rebuilding. I'm skeptical that it will succeed as it failed on Debian. If it fails I can just restore the Ubuntu patches that did work. I wish I had a better way of testing ARM than pushing a build and seeing what happens....

Anyway, as long as you don't do a dist-upgrade today, you'll be fine. Thursday started the first sync from Debian unstable so it was a bad time to dist-upgrade anyway.

---

### Post by Harry33 on 2012-05-27
The new update gnome-shell_3.4.1-1ubuntu2 solves this issue.

---

### Post by zika on 2012-05-27
> **Harry33 said:**
> The new update gnome-shell_3.4.1-1ubuntu2 solves this issue.But Cinnamon is still in trouble... ;)
Yes, I have moved to quantal-branch in nightly... ;)

Update&#8321;: Solved by the upgrade (dist, of course)...

---

