---
title: "Mediawiki package broken"
date: 2006-12-30
forum: Repositories &amp; Backports
---

### Post by ryharv on 2006-12-30
Hi all,

The mediawiki package appears to be broken and I cannot install mediawiki via apt.  I've seen another user complain of the same issue on another thread but thought the issue deserved its own thread.  Here is the error message I get:

```
sudo apt-get install mediawiki
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
  mediawiki: Depends: mediawiki1.7 but it is not installable
             Depends: mediawiki1.7-math but it is not installable
E: Broken packages
```

The error message instructs me to file a bug report -- I'm not sure how to do this.  Ideas?

Thank you,

  Ryan Harvey

---

### Post by tarpon_bill on 2007-01-05
I was going to give mediawiki a try, this doesn't look good.

---

### Post by julioromano on 2007-01-14
I'm having the same problem.

A bug can be filed here:
[https://bugs.launchpad.net/ubuntu/edgy/+bugs](https://bugs.launchpad.net/ubuntu/edgy/+bugs)

---

