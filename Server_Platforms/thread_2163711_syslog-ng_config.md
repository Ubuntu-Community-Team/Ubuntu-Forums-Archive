---
title: "syslog-ng config"
date: 2013-07-19
forum: Server Platforms
---

### Post by sosytee on 2013-07-19
I have installed syslog-ng to the ubuntu server. I now need to enter the configuration file. I attempting to do it using ```
sudo/etc/syslog-ng/syslog-ng.conf
``` the response i get is permission denied. How can i rectify this problem?

---

### Post by codemaniac on 2013-07-19
*Thread moved to **Server Platforms**.*

---

### Post by DeathByDenim on 2013-07-19
That's not quite right. /etc/syslog-ng/syslog-ng.conf is a text file. It's not an executable. So you need to type
```
sudo nano -w /etc/syslog-ng/syslog-ng.conf
```
(Or use vi instead of nano or whatever your favourite text editor is)

---

