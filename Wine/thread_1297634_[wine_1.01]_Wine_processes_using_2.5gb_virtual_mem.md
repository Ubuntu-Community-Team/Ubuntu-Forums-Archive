---
title: "[wine 1.01] Wine processes using 2.5gb virtual memory each"
date: 2009-10-22
forum: Wine
---

### Post by katana1000 on 2009-10-22
when I run any app in wine , the related processes, winedevices, services, and explorer.exe all use 2.5gb virtual memory EACH..

Earlier I thought this was only due to a game, but now its turning up for any wine app I am runnign.

please suggest a solution to solving this problem

---

### Post by hikaricore on 2009-10-22
Sounds like a memory leak, what have you done to your WINE installion?
Dll overrides?  Custom patches?  Anything weird?
Try with a new wine prefix and see if it results in the same issue.

---

### Post by katana1000 on 2009-11-11
I reinstalled karmic fresh, and installed wine beta.

[IMG]http://img692.imageshack.us/img692/4850/screenshotcc.png[/IMG]

the issue is still not addressed

---

