---
title: "rosegarden4 dependencies in dapper"
date: 2006-07-01
forum: The Cafe
---

### Post by blizzrdof77 on 2006-07-01
hi everyone.  i tried adding this repository to my sourcest.list so i could install rosegarden4 on dapper drake...

deb [http://ubuntu.lnix.net/dapper/](http://ubuntu.lnix.net/dapper/) ./

after doing so, i tried installing rosegarden4 and this was my error message...
```

alex@alex-laptop:/etc/apt$ sudo apt-get install rosegarden4
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  rosegarden4: Depends: libjack0.100.0-0 (>= 0.100.0) but it is not installable
               Depends: liblo0 (>= 0.22) but it is not installable
               Depends: liblrdf0 but it is not installable
               Depends: jackd but it is not installable
E: Broken packages

```

---

