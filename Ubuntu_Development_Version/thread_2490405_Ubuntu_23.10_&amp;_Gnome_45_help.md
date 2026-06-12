---
title: "Ubuntu 23.10 &amp; Gnome 45 help"
date: 2023-09-02
forum: Ubuntu Development Version
---

### Post by mpmckinnon on 2023-09-02
Hi there I am not sure were to ask this question so if it's in the wrong spot I am sorry. Currently I am running Ubuntu 23.10 with now updated to Gnome 45 beta. A few days after that started to get this error message.

E: Conflicting values set for option Signed-By regarding source [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) mantic-security: /usr/share/keyrings/ubuntu-archive-keyring.gpg != 
E: The list of sources could not be read.

Never seen it before wondering if someone else might have?

Thank You
Mark McKinnon

---

### Post by TheFu on 2023-09-02
23.10 hasn't been released, so the appropriate place to as any questions related to alpha code is in the Ubuntu-Next sub-forum.  I think they call it "Development Release" here.

---

### Post by ajgreeny on 2023-09-03
Moved to Development Version section which is more appropriate for this query.

---

### Post by corradoventu on 2023-09-03
You may have /etc/apt/sources.list in the new deb822 format. See explain in bug [https://bugs.launchpad.net/subiquity/+bug/2033900](https://bugs.launchpad.net/subiquity/+bug/2033900)

---

