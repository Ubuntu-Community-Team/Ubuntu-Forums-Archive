---
title: "Landscape private, never loads new inital user."
date: 2017-01-04
forum: Ubuntu Cloud and Juju
---

### Post by phalen on 2017-01-04
I have tried installing landscape on 14.4 and 16.4  both times I get to the new user creation page and then after clicking submit it just hangs. [https://server/new-standalone-user](https://server/new-standalone-user) I see nothing in any of the landscape logs nor did i run out of space etc.  I am at a loss as to how I should trouble shoot.

---

### Post by phalen on 2017-01-05
well this issue was solved by a stupid answer.  one must have a fqdn working for the server to properly finish creating the administrative account. I had given the os a fqdn when I originally installed ubuntu with intention of adding it to dns and such later on if i decided to continue using landscape.  for temporary sake I had entered just the hostname in the hosts file and or launched via ip wich neither worked right.   after adding the fqdn to the hosts file it now created normally.

---

