---
title: "which directories can be seen by the public?"
date: 2007-12-07
forum: Server Platforms
---

### Post by winstonzeng on 2007-12-07
i was just wondering is /var/www/ the only directory that can be viewed by public? i want to know this so i can upload my .htpasswd and config files to a private directory instead of a public one.

also if people use website downloading programs or the wget command, do they only download the files under /var/www/?

---

### Post by gaten on 2007-12-07
By default, yes. And every subdirectory inside /var/www.

You can change this in your Apache configuration (I assume you're using Apache) if you so desire.

---

### Post by winstonzeng on 2007-12-07
so only /var/www/ can be downloaded and viewed? what about the /var/ directory, is it private or public?

---

### Post by gaten on 2007-12-07
/var is private. You should check out some Apache docs, they will give you a better understanding of what's going on.

---

