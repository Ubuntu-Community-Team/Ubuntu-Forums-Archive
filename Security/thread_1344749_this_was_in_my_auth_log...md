---
title: "this was in my auth log.."
date: 2009-12-03
forum: Security
---

### Post by jessiebrownjr on 2009-12-03
Dec  2 14:04:50 desktop groupadd[4495]: new group: name=smmta, GID=124
Dec  2 14:04:50 desktop useradd[4501]: new user: name=smmta, UID=112, GID=124, home=/var/lib/sendmail, shell=/bin/false
Dec  2 14:04:50 desktop usermod[4508]: change user `smmta' password
Dec  2 14:04:51 desktop chage[4513]: changed password expiry for smmta
Dec  2 14:04:51 desktop chfn[4516]: changed user `smmta' information
Dec  2 14:04:51 desktop groupadd[4524]: new group: name=smmsp, GID=125
Dec  2 14:04:51 desktop useradd[4530]: new user: name=smmsp, UID=113, GID=125, home=/var/lib/sendmail, shell=/bin/false
Dec  2 14:04:52 desktop usermod[4535]: change user `smmsp' password
Dec  2 14:04:52 desktop chage[4540]: changed password expiry for smmsp
Dec  2 14:04:52 desktop chfn[4543]: changed user `smmsp' information

Is this normal? I see that it happened within a few seconds of each other, and also my MTA daemon turned on.. The only thing I installed prior to seeing the MTA daemon turn itself on was the tiger rootkit checker from the forums here, as well as updates and GUFW. Help, was I comprimised or did tiger do this?

---

### Post by cdenley on 2009-12-03
sendmail is recommended by tiger. sendmail-base is a dependency of sendmail. The post-installation script for sendmail-base creates those users and groups.

---

### Post by jessiebrownjr on 2009-12-03
> **cdenley said:**
> sendmail is recommended by tiger. sendmail-base is a dependency of sendmail. The post-installation script for sendmail-base creates those users and groups.

thanks for the heads up!

---

