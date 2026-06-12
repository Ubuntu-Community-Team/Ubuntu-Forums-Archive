---
title: "Recommended Gutsy repository list?"
date: 2007-10-23
forum: Repositories &amp; Backports
---

### Post by Rehdon on 2007-10-23
Hi guys, has anyone proposed a recommended repo list for gutsy? I understand it's less necessary since the creation of the restricted extras, but still something interesting could be found elsewhere.

Rehdon

---

### Post by bapoumba on 2007-10-23
I'mnot sure what you are looking for, but I just stick to ubuntu-supported repos, and medibuntu for some codecs.

---

### Post by mibadt on 2007-10-24
Hi,

Either use source-o-matic, or copy mine (Germany):
# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy main restricted
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy universe multiverse
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse

deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe multiverse

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse

----------

Regards,
Michael Badt

---

### Post by 1337455 10534 on 2007-11-10
I think he meant one that is more expansive than even trevinos for feisty.

---

### Post by leader303 on 2007-11-10
i'm sure there are more good repos out there on the web, but for some reason i have failed to find them. what i'd love to see is a list of your favourite repos with short description, what's inside.

---

### Post by ViRMiN on 2007-11-10
Having had many conflicts from using several third-party repos on Fedora, I stick to the selectable repos on Ubuntu including Universe, and have added Medibuntu for codecs, just as bapoumba says... no problems whatsoever...

---

### Post by 1337455 10534 on 2007-11-11
Yes, but, for example, Pidgin didnt upgrade to 2.2.2 automatically, and neither does rythmbox (on feisty anyway) or Audacity...

---

