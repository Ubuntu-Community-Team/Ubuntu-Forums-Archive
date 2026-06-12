---
title: "Wine COM ports"
date: 2010-12-01
forum: Wine
---

### Post by wolfgangmcq on 2010-12-01
I am trying to set up a Windows program that needs to get at the COM ports. I figured out that I need to put a symlink in ~/.wine/dosdevices called com1, so I ran ```
ln -s /dev/ttyS0 ~/.wine/dosdevices/com1
``` and made a symlink. This did not help; I still can't access the port in Wine. Any suggestions?

---

