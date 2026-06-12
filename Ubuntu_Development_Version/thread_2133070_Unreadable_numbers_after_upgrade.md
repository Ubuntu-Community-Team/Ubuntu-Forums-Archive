---
title: "Unreadable numbers after upgrade"
date: 2013-04-06
forum: Ubuntu Development Version
---

### Post by tomasz_svk on 2013-04-06
Hi,
i have upgraded Ubuntu 12.10 to 13.04 about month ago. In short time I spotted, that some numbers in programs are unreadable (ie. Skype, qBitTorrent and more). I tried to regenerate font cache and locales but with no success. It's looks like the problem is only with numbers in specified format, like time, etc... 

```

$ localeLANG=sk_SK.UTF-8
LANGUAGE=sk:en_US:en
LC_CTYPE="sk_SK.UTF-8"
LC_NUMERIC=sk_SK.UTF-8
LC_TIME=sk_SK.UTF-8
LC_COLLATE="sk_SK.UTF-8"
LC_MONETARY=sk_SK.UTF-8
LC_MESSAGES="sk_SK.UTF-8"
LC_PAPER=sk_SK.UTF-8
LC_NAME=sk_SK.UTF-8
LC_ADDRESS=sk_SK.UTF-8
LC_TELEPHONE=sk_SK.UTF-8
LC_MEASUREMENT=sk_SK.UTF-8
LC_IDENTIFICATION=sk_SK.UTF-8
LC_ALL=



```

---

### Post by Triptaminer on 2013-06-06
hmm... it looks like problem only with slovak translate :/ i got same problem and this is only one treat, what i found... please anybody has some ideas how to fix it? :(

EDIT: thanks for your post, now i found this bug in:

[https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/1173138](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/1173138)

as i wrote above, this error is only in slovak localization in Qt4 apps. it uses arabic-indic numbers instead arabic :/ now we must hope to fast fix... or is there any workaroud?

---

### Post by minoo1 on 2013-06-26
This helped me with the problem:
[http://askubuntu.com/questions/310990/borked-encoding-in-ubuntu-13-04-for-slovak-language](http://askubuntu.com/questions/310990/borked-encoding-in-ubuntu-13-04-for-slovak-language)

Numbers are now okay

---

### Post by Triptaminer on 2013-06-27
thank you, this one works like charm :)

---

