---
title: "Extra Repositories? 5.10 Breezy"
date: 2005-10-16
forum: Repositories &amp; Backports
---

### Post by zrothe on 2005-10-16
What are the extra repositories that can be added to the sources list? I hear people saying multiverse universe, etc. None of this means anything to me, I don't know where to find them. Thanks.

---

### Post by RastaMahata on 2005-10-16
the sources list is located at **/etc/apt/sources.list**
you should update this list witht e extra repositories.
My list is as follows:```
#Breezy Main
deb http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
#Breezy Security
deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted universe multiverse
#Breezy Updates
deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
#Backports
#deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
#deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
#CipherFunk
deb ftp://cipherfunk.org/pub/packages/ubuntu breezy main
```

---

