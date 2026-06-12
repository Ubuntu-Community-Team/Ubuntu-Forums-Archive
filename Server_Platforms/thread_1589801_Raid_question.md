---
title: "Raid question"
date: 2010-10-06
forum: Server Platforms
---

### Post by tubaguy50035 on 2010-10-06
Can I use UUIDs to setup a raid with mdadm?

---

### Post by doogy2004 on 2010-10-07
This thread has been marked as [SOLVED], what was the resolution?

---

### Post by tubaguy50035 on 2010-10-07
Oh.  I found out that if you use mdadm, it goes ahead and keeps track of the drives for you without relying on the letters (sda, sdb, etc.).  I have yet to test this out!  So don't take my word for it, but it is on the internet, just required really deep searching.  My raid will be done building in the next half hour.  I'll try to remember to post back here whether you can have those letters change or if it doesn't work.

---

### Post by tubaguy50035 on 2010-10-07
Just to confirm, mdadm will keep track of the drives used in the arrays no matter what letter they get assigned upon boot.  Just make sure you configure mdadm.conf correctly

---

