---
title: "question about update settings"
date: 2012-01-05
forum: System76 Support
---

### Post by icamefromouterspace on 2012-01-05
i just got my system76 lemur3 laptop.. i was about to run the update tool but i checked out the software sources screen first. By default "unsupported updates (oneiric-backports)" was selected. Normally i never check this because i figure "why would i want an unsupported update?". but system 76 has this selected by default.

is this because this needs to be on to keep their drivers up to date or something? or should i be fine unchecking it?

---

### Post by 2F4U on 2012-01-06
The backports repository has newer versions of already installed packages. Without backports, you will just get security updates for existing packages, but not newer versions. If you are fine with that or don't want to risk instability, disable backports. It is by default enabled in all Ubuntu installations and has, as far as I know, nothing to do with System 76.

---

### Post by isantop on 2012-01-06
I don't think there's anything required from the backports, so you should be fine to disable it. It comes enabled by default in Ubuntu; we don't specifically enable it.

---

