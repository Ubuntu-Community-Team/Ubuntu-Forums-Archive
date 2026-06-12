---
title: "Almost 100% cpu usage all the time."
date: 2017-01-26
forum: Server Platforms
---

### Post by pixel2 on 2017-01-26
Ive switched from Debian 7 to Ubuntu Server (works like a charm) but Ive noticed that htop shows almost 100% usage of all 4 cores all the time (= even if Im the only user logged-in doing nothing). Its strange in the way that, when I log in from my testuser (no-root), htop shows real cpu usage.

Whats wrong here?

---

### Post by ajgreeny on 2017-01-26
You do not tell us what process is using the 100% of cpu resources, so we have no idea at all what's wrong.

Give us more info please and we'll do our best to assist.

---

### Post by cariboo on 2017-01-26
> **pixel2 said:**
> Ive switched from Debian 7 to Ubuntu Server (works like a charm) but Ive noticed that htop shows almost 100% usage of all 4 cores all the time (= even if Im the only user logged-in doing nothing). Its strange in the way that, when I log in from my testuser (no-root), htop shows real cpu usage.

Whats wrong here?


It would help if you showed us a screenshot of htop.

---

### Post by pixel2 on 2017-02-19
issue solved. It was one RAM chip that was broken and it was giving out false data. Changed that chip and all is ok now.

---

