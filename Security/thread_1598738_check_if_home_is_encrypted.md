---
title: "check if /home is encrypted"
date: 2010-10-16
forum: Security
---

### Post by marks_linux on 2010-10-16
I'm using Kubuntu 10.10 and I'm pretty sure I opted for an encrypted /home is there a easy way to check it is in fact encrypted.

All I'm trying to achieve is security of the files etc on a laptop in case it is stolen.

---

### Post by FuturePilot on 2010-10-16
```
mount | grep ecryptfs
```

---

### Post by marks_linux on 2010-10-16
awesome - thank you!

---

### Post by HermanAB on 2010-10-17
...and of course, you can log out and then try to read your data with a hex editor.

---

### Post by tubbygweilo on 2010-10-17
You could also switch off and boot via a live cd to see if you can make head or tail of the /home directory on your hard disk thus simulating some sort of attack on your kit.

---

