---
title: "Do Different Versions Of Ubuntu Issue updates at the same time?"
date: 2020-11-30
forum: Ubuntu, Linux and OS Chat
---

### Post by O)9(yo&amp;# on 2020-11-30
Probably a stupid question, but it occurred to me today. I run Ubuntu 16.04.7 and Bodhi 5. Bodhi 5 is based on Ubuntu 18. So, if Ubuntu 16 issues an update, does that mean Ubuntu 18 also does - and thus Ubuntu-based distros, such as Bodhi, also do?

---

### Post by CatKiller on 2020-11-30
Not in general, no. Ubuntu releases don't, in general, get updates as such. What they get are backported fixes for security or other bugs, cherry-picked from the later versions. Since the versions that are being backported to are different for different supported releases, the updates are somewhat independent.

The Ubuntu flavours will all get those updates at the same time, since they use the same repositories. Distributions that are based on Ubuntu have their own repositories, and they'll pick and choose which updates to the Ubuntu repositories that they want to put in their own.

---

### Post by O)9(yo&amp;# on 2020-12-01
Thanks, that clarifies the issue for me.:p

---

