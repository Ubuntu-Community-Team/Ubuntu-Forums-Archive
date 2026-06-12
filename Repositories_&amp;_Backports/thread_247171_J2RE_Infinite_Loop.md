---
title: "J2RE Infinite Loop"
date: 2006-08-30
forum: Repositories &amp; Backports
---

### Post by fabulous_mr_e on 2006-08-30
Hello there!
I've been using Ubuntu on and off for the past year but have finally taken the leap and installed it on my primary machine as a development environment for University.

I've been playing around with the Sun java packages trying to find a combination of packages and an IDE that will suit me but have stumbled across  a problem that's driving me up the wall.

I started this seemingly endless cycle by installing and then removing the blackhawk 1.4 jre that

I am unable to install the sun-java5-jre package because:
```
sun-java5-jre depends on sun-java5-bin (= 1.5.0-08-1) | ia32-sun-java5-bin (= 1.5.0-08-1); however:
  Package sun-java5-bin is not configured yet.
  Package ia32-sun-java5-bin is not installed.
dpkg: error processing sun-java5-jre (--install):
```

however when I attempt to install, remove or modify the sun-java5-bin package I am greeted with:

```
dpkg: dependency problems prevent configuration of sun-java5-bin:
 sun-java5-bin depends on sun-java5-jre (= 1.5.0-08-1); however:
  Package sun-java5-jre is not configured yet.
dpkg: error processing sun-java5-bin (--install):
 dependency problems - leaving unconfigured
```

When I run an apt-get remove on sun-java5-bin I am told:
```

dpkg: dependency problems prevent configuration of sun-java5-bin:
 sun-java5-bin depends on sun-java5-jre (= 1.5.0-08-1); however:
  Package sun-java5-jre is not configured yet.
dpkg: error processing sun-java5-bin (--install):
 dependency problems - leaving unconfigured

```

and any combination of removing or cleaning or autocleaning my package list doesnt seem to shift it. It appears to be installed but not configured and pretty much point blank refuses to be removed. I'd appreciate a hand :D.

Thank you in advance.
XXe

---

### Post by fabulous_mr_e on 2006-08-30
Never mind :)
Sorted it out by removing everything i could find related to these packages and then reinstalling them. Put it down to snow-blindness and lack of sleep.

---

