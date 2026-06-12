---
title: "Different sudo su password"
date: 2016-10-19
forum: Server Platforms
---

### Post by espressobeanmachine on 2016-10-19
I have Ubuntu server with no desktop environment running, I have ssh running with permitrootlogin set to "no" i have a user that can sudo su but is it possible to require that the sudo su password is different than the user's own password? Meaning one password for that user to login and another password for sudo?

---

### Post by darkod on 2016-10-19
No, the password is always the same. There is only one password for the user. Whether that user can run sudo commands depends on whether he is in the sudo group or not, but the password is one and only.

---

### Post by SeijiSensei on 2016-10-20
We can't tell you how to do it here, but it is possible to set a password for the root user.  The user would then need to know both her own password and the one for root.  See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo).  If you do this, you would need to disable the sudo mechanism for that user.

---

