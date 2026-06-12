---
title: "pam_radius_auth issue"
date: 2014-10-22
forum: Security
---

### Post by patdaman45 on 2014-10-22
I am having some trouble getting the radius_auth module for pam working.  I have configured /etc/pam_radius_auth.conf with the correct server ip and secret but when trying to login using sshd, auth.log says that radius returned code 3 (reject).  When using radtest with the same info, i get an accept code.

At this point I am fairly sure that the radius server is working but the pam module is not communicating correctly with it.  Any help would be awesome!

---

