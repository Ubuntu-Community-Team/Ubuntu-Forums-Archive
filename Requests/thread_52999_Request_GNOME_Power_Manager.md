---
title: "Request: GNOME Power Manager"
date: 2005-07-29
forum: Requests
---

### Post by vvlist on 2005-07-29
I like many other users run Ubuntu on a laptop. I find it difficult to adjust power settings, and I don't get very good battery life, well not as much as my centrino is capable of.  :-|   Sadly there are some dependencies that are not satisfied for the 0.1.0 release, so I was wondering, are they in breezy, and can they be ported back? Thanks.

---

### Post by Burgundavia on 2005-08-01
G-p-m has some nasty deps, and some lowerlevel stuff that might make it almost impossible to backport.

Corey

---

### Post by vvlist on 2005-08-01
Yeah, I thought it would be nasty. I just wanted to ask just in case, thanks.

---

### Post by Burgundavia on 2005-08-01
It would need a new version of Dbus and new version of HAL and every application that uses those would need to be updated. 

Corey

---

