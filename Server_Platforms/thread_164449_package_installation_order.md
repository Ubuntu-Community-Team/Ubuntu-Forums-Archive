---
title: "package installation order"
date: 2006-04-22
forum: Server Platforms
---

### Post by gymsmoke on 2006-04-22
I installed spamassassin for my server, and apt attempted to configure dcc-client before installing/configuring dcc-common. (I saw the same problem in clamav).
To fix this, can I just dpkg -reconfigure dcc-client?

---

### Post by Sutekh on 2006-04-23
Yep, just with no space between dpkg and -reconfigure
```
sudo dpkg-reconfigure dcc-client
```
Will reconfigure the package

---

