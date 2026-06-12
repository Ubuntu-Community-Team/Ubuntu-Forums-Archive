---
title: "Rkhunter /usr/bin/curl Warning"
date: 2010-05-09
forum: Security
---

### Post by User3k on 2010-05-09
I did some research on this but didn't find anything specific. I am pretty sure this is a false positive, but I thought I would ask here just to make sure. I never had this one come up before when I used rkhunter, so it is better being safe then sorry, lol.

Rkhunter:
> /usr/bin/curl                                                         [ Warning ]


Ubuntu 10.04


Chkrootkit didn't find anything.

---

### Post by unspawn on 2010-05-09
> **User3k said:**
> I did some research on this but didn't find anything specific.
See the rkhunter.log. Verify the alert is a "false positive", then check your rkhunter.conf for white-listing options and examples. If unclear see the docs (there's an entry and even a command for adding white-listing entries). If that doesn't do it search the rkhunter users mailing list archives for examples (or this forum).

* Also please note most questions wrt RKH have already been answered in the rkhunter users mailing list archives.

---

### Post by User3k on 2010-05-09
> **unspawn said:**
> See the rkhunter.log. Verify the alert is a "false positive", then check your rkhunter.conf for white-listing options and examples. If unclear see the docs (there's an entry and even a command for adding white-listing entries). If that doesn't do it search the rkhunter users mailing list archives for examples (or this forum).

* Also please note most questions wrt RKH have already been answered in the rkhunter users mailing list archives.

Thanks. I was half asleep when I posted this. I will check out the rkhunter users mailing list archives as well.

---

