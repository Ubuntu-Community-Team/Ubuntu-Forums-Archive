---
title: "Why is LibreOffice trying to access my Thunderbird profile folder ?"
date: 2018-09-01
forum: Security
---

### Post by linuxyogi on 2018-09-01
```
[ 8902.045381] audit: type=1400 audit(1535819120.102:44): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/home/ubuntu/.thunderbird/profiles.ini" pid=11923 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
[ 8902.048682] audit: type=1400 audit(1535819120.106:45): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/home/ubuntu/.thunderbird/p6o5eo3f.default/secmod.db" pid=11923 comm="soffice.bin" requested_mask="r" denied_mask="r" fsuid=1000 ouid=1000
[ 8902.049760] audit: type=1400 audit(1535819120.106:46): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/home/ubuntu/.thunderbird/p6o5eo3f.default/cert8.db" pid=11923 comm="soffice.bin" requested_mask="wr" denied_mask="wr" fsuid=1000 ouid=1000
[ 8902.050154] audit: type=1400 audit(1535819120.106:47): apparmor="ALLOWED" operation="open" profile="libreoffice-soffice" name="/home/ubuntu/.thunderbird/p6o5eo3f.default/key3.db" pid=11923 comm="soffice.bin" requested_mask="wr" denied_mask="wr" fsuid=1000 ouid=1000

```

Why is LibreOffice trying to access my Thunderbird profile folder ?

---

### Post by linuxyogi on 2018-09-02
Bump

---

### Post by linuxyogi on 2018-09-11
Bump

---

### Post by zestysoft on 2019-06-05
Libreoffice uses the certs that Mozilla stores for signing, etc:
[https://weekly-geekly.github.io/articles/357692/index.html](https://weekly-geekly.github.io/articles/357692/index.html)
if you don't want this you can enable that apparmor rule:
sudo aa-enforce /etc/apparmor.d/usr.lib.libreoffice.program.soffice.bin

---

