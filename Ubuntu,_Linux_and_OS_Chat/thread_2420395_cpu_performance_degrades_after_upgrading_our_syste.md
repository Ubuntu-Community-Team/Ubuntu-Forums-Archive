---
title: "cpu performance degrades after upgrading our systems from 12.04 to 18.04"
date: 2019-06-04
forum: Ubuntu, Linux and OS Chat
---

### Post by skatuku on 2019-06-04
Hello,

We are a networking company who mostly rely on TCP and UDP calls within our application and we upgraded our OS from Ubuntu 12.04 (Precise Pangolin) to 18.04 (Bionic Beaver), we see performance issues with high CPU and Memory utilization reaching 100%. Has anyone faced similar kind of issues?

Thanks!

---

### Post by linuxyogi on 2019-06-05
> **skatuku said:**
> Hello,

We are a networking company who mostly rely on TCP and UDP calls within our application and we upgraded our OS from Ubuntu 12.04 (Precise Pangolin) to 18.04 (Bionic Beaver), we see performance issues with high CPU and Memory utilization reaching 100%. Has anyone faced similar kind of issues?

Thanks!

Was this a fresh installation of 18.04 ? Or was it a in place upgrade.

If it was a in place upgrade I am not sure how you managed to do that

because 12.04 is out of support a long time back.

---

### Post by mastablasta on 2019-06-05
check with top or htop what is taking over the CPU. 

i don't have this issue on server. in fact CPU barely has work to do (nextcloud).

---

