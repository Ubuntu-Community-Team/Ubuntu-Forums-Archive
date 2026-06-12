---
title: "Reducing high I/O wait times"
date: 2006-09-12
forum: Server Platforms
---

### Post by FakeOutdoorsman on 2006-09-12
Besides buying a new hard drive, what are the best ways to reduce high I/O wait times and reduce high reads/writes per second on a server running database driven applications?

---

### Post by souki on 2006-09-13
maybe this :

- disk tunning (hdparm, kernel)
- more RAM
- database cache, buffer, shared memory tunning
- table's structure, field's size, indexes
- reduce number of connections (web app?)
- application level (if you've designed it)

---

### Post by FakeOutdoorsman on 2006-09-13
Thanks for the info.  I think adding more RAM and another hard drive might be the solution right now.

---

### Post by rastilin on 2006-09-15
Why not change the disk scheduler to something designed for less latency like "deadline"?

---

