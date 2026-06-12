---
title: "Trouble refreshing snaps"
date: 2019-02-13
forum: Ubuntu Development Version
---

### Post by zika on 2019-02-13
```
:~$sudo snap refresh
error: cannot refresh: Post https://api.snapcraft.io/v2/snaps/refresh: dial tcp 91.189.92.41:443:
connect: connection refused
```

---

### Post by PaulW2U on 2019-02-13
Some snap services down or interrupted: [https://status.snapcraft.io/](https://status.snapcraft.io/)

---

### Post by zika on 2019-02-13
Looking deeper...```
:~$ curl https://api.snapcraft.io/api/v1/snaps/assertions/snap-declaration/16/jZLfBRzf1cYlYysIjD2bwSzNtngY0qit?max-format=3type: snap-declaration
format: 2
authority-id: canonical
revision: 4
series: 16
snap-id: jZLfBRzf1cYlYysIjD2bwSzNtngY0qit
publisher-id: canonical
slots:
  content:
    allow-auto-connection:
      -
        plug-attributes:
          content: $SLOT(content)
        slot-attributes:
          content: gtk-3-themes
      -
        plug-attributes:
          content: $SLOT(content)
        slot-attributes:
          content: icon-themes
      -
        plug-attributes:
          content: $SLOT(content)
        slot-attributes:
          content: sound-themes
      -
        plug-attributes:
          content: $SLOT(content)
        slot-attributes:
          content: gtk-2-themes
snap-name: gtk-common-themes
timestamp: 2018-11-16T19:08:04.578869Z
sign-key-sha3-384: BWDEoaqyr25nF5SNCvEv2v7QnM9QsfCc0PBMYD_i2NGSQ32EF2d4D0hqUel3m8ul


AcLBUgQAAQoABgUCW+8VlAAAtQsQADwKP65uAka7UUXI1h6hyevTCKQNrtlw+qXB45+Ndz/LUV8V
gXNujoqGwaGTcG5o+bmPZDv6TF9XWeJXhCy2uwkt0D22hIrYoWPoD7PWP4PHzzQyrWtJmxH18DGC
8g0IxetUmLNQ6dJdHgBFWK/lbtepRZolro0JrIWE/zpl265TFIfMaiuh3G5naNLqJbd6FsjfBEYJ
CpmsDH7nJR2jjH3ArdaVZB8N+J93oRHu74GN6WR0WODq+XyFVB9RxwskEBGivub9+NzTtNKBRxqE
Vs5CItmrZCcGhzODmeqa9fC7irEDGIjgK1CBvBlJWH71lpAZxzD2kAkaPtt6fwI1NxPZy6okuW2h
qejOreLe8g9gHWiYQJZYAhBeCRiPHhJ0iVCsUDDh7BNex93eDmNJxL3MP0XjZ2spDlpsJ3BQMPI7
DWHNrN4g/uUyWhsGxzwfNZ8RBwNYagYDEucHMa9drRA8tYb8BpHsJDyLQocrangM5mo/u3WKlo/x
/bMTHue+AO4Q0vTgr8qPPsfzbyF29tyAcNAVcPxJsB4jN/o+4fNb/OAWK4vZATxE8JakQwNuFrof
DACJB473aEL8cAOCeNkyWq47i6j7qGIYur49Fevn+TTX4x1Iyh0TsKQWVRxXLxHSwJdZ4livLVMK
YDSZ79vZHX1Xa1ssy4+CpcUqiOJj
```

---

### Post by zika on 2019-02-13
> **PaulW2U said:**
> Some snap services down or interrupted: [https://status.snapcraft.io/](https://status.snapcraft.io/)Thanks. Nice to see that I'm not to blame... As I am 99.9% of time...
Update&#8321;:```
:~$ sudo snap refresh
All snaps up to date.
```
Thanks, again...

---

