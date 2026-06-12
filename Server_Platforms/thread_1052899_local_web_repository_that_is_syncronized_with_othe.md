---
title: "local web repository that is syncronized with other major repository"
date: 2009-01-28
forum: Server Platforms
---

### Post by m_alnaanah on 2009-01-28
Hi everyone,


I want to make a local repository on my web server so all of my friend can use it. But I want this repository to be synchronised with a major one. but with certain cache size, so it will download the package from the major repository (whenever it's requested by a user)  and cache it for future use.


Also I have limited cache size on my server (lets say 2 Gigas).

can any one help please.

---

### Post by Sam Lars on 2009-01-28
You can install apt-cacher-ng.  You can then point all computers that you want to use it with to that computer, and it will cache the update lists and package files for you.

---

### Post by m_alnaanah on 2009-01-29
Thanks alot, work in progress.

---

