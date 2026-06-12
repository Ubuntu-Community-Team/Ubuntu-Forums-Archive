---
title: "[SOLVED] Windows Xp limited user account internet access problem!"
date: 2008-07-08
forum: Windows
---

### Post by Rytron on 2008-07-08
Hi,
I have a Windows Xp desktop. I want to use a limited account(for more security) for connecting to the internet via a wireless connection. However when I try to connect from my limited user account; it keeps connecting and then dropping. 

When I try to connect from my administrator user account there are no problems connecting and it doesn't drop.

Very strange. Has anyone suggestions to solve this?

Thanks.

---

### Post by pofigster on 2008-07-08
Are you trying to use a WINDOWS limited user account to connect to the internet?

---

### Post by tamoneya on 2008-07-08
i have similar problems on my parents computer (still working on getting them to ubuntu).  I just wrote a batch script called "fix internet.bat" and left it on the desktop.  It just contained two lines:```
ipconfig /release
ipconfig /renew
```
I just told them to click it in order to "restart the internet"

---

### Post by Rytron on 2008-07-08
> **pofigster said:**
> Are you trying to use a WINDOWS limited user account to connect to the internet?

Yes.

---

### Post by Rytron on 2008-07-09
> **tamoneya said:**
> i have similar problems on my parents computer (still working on getting them to ubuntu).  I just wrote a batch script called "fix internet.bat" and left it on the desktop.  It just contained two lines:```
ipconfig /release
ipconfig /renew
```
I just told them to click it in order to "restart the internet"

Hi,
I tried your method but no joy.
I finally got it working though. It was either by using 'repair' or else it was by not having Windows automatically connect. It now connects on 'demand'.
Cheers.
:popcorn:

---

