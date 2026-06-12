---
title: "KlamAV 0.46"
date: 2009-11-26
forum: Security
---

### Post by kree8or on 2009-11-26
Hi,I'm using KlamAV0.46 for my av needs, but when i go to update the signatures, the "update" button is  greyed out.Any ideas how to up date my AV.(i'm using 9.10 btw)

---

### Post by cariboo on 2009-11-26
Klamav is just a gui front end for clamav. have you run:

```
sudo freshclam
```

This runs a utility that checks for new virus definitions once every hour.

---

