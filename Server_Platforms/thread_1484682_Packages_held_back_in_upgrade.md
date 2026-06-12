---
title: "Packages held back in upgrade?"
date: 2010-05-16
forum: Server Platforms
---

### Post by Loki57701 on 2010-05-16
I recently upgraded to 10.04 (clean install) and when I run apt-get upgrade, I get:

```

The following packages have been kept back:
  linux-headers-server linux-image-server linux-server
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.


```Anyone know why these updates have been held back?

---

### Post by Bachstelze on 2010-05-16
You need

```
sudo apt-get dist-upgrade
```

Do a forums search if you want to know why, this has been asked countless times.

---

