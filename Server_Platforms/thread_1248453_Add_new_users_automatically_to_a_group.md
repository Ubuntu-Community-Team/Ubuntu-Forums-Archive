---
title: "Add new users automatically to a group"
date: 2009-08-24
forum: Server Platforms
---

### Post by gypsumwolf on 2009-08-24
I created a group "nfb" with nproc limits. Can I have it automatically put the new users into the "nfb" group without me having to manually add them?
If I get lots and lots of new users it would get quite time consuming to add them all to 1 group manually unless there is a command to add everyone to a group without having to do them all individually.

---

### Post by windependence on 2009-08-24
You can use the /etc/skel to control how a new user is created.

-Tim

---

