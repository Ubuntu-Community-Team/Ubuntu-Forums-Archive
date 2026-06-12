---
title: "Deluge - maximum half-open connections"
date: 2009-10-07
forum: The Cafe
---

### Post by afeasfaerw23231233 on 2009-10-07
Just discover that changing maximum half-open connections to -1 increases the speed to 1.3MB/s (the maximum my ISP provides). With the default setting (50), I could get no more than 800KB/s. Why is that?

---

### Post by FuturePilot on 2009-10-07
Because -1 sets it to no limit. So you can have as many half-open connections as possible. Some routers don't like getting loaded up with half-open connections though. Though I'm not sure how this could increase speed as a half-open connection just means that one end of the connection has died without notifying the other end.

---

