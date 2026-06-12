---
title: "I delete &quot;etc/init.d/lighttpd&quot; by mistake!"
date: 2008-07-08
forum: Server Platforms
---

### Post by ablmf on 2008-07-08
Re-install lighttpd by apt-get doesn't restore that file?

What can I do?

---

### Post by p_quarles on 2008-07-08
It might work to run this:
```
sudo dpkg-reconfigure lighttpd
```
If that by itself doesn't work, you may try renaming any configuration files in /etc and then running the above again. The key is to finding the condition at which the system knows it needs to generate the first-run information. Removing stuff should get it there eventually.

---

