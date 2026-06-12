---
title: "Prevent desktop background from showing on login screen"
date: 2012-04-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Nick Payne on 2012-04-02
If I change the logged-in desktop background to one of my photos, 12.04 defaults to also using the same photo as background for the login screen. Is it possible to stop the login screen getting changed when I change the desktop background?

---

### Post by mc4man on 2012-04-02
Simply change the permissions of the file you're using as your Background
-rw-r----- will do (remove read from 'Others'

---

