---
title: "How do I know apparmor is working properly?"
date: 2012-11-02
forum: Security
---

### Post by arroy_0209 on 2012-11-02
I keep apparmor in enforced mode but it works silently. The only place where its effects are seen are in log files where profile-replace or profile-loaded type messages are found. How do I know that is is really working the way it is supposed to do? NoScript, for example is easy to feel since often I have to let noscript allow some particular website to load in firefox otherwise it simply won't load. Is there any such way in which working of apparmor can be understood or tested?

---

### Post by jerome1232 on 2012-11-02
Try to download a file to an area that apparmor says is off limits but your user has access to, it should error out and not let you download the file.

---

