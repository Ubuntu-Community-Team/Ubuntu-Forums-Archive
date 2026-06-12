---
title: "I see oss-compat is still being kep back"
date: 2012-06-27
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by philinux on 2012-06-27
```
The following packages have been kept back:
  oss-compat
```

Not a big deal.

---

### Post by dino99 on 2012-06-27
The purpose of this package is for applications that only support OSS
to depend on it, hence preventing common "/dev/dsp not found" errors
that would confuse unexperienced users.


Latest update:
Mon, 05 Mar 2012 17:02:54 +0100

so you might not, like me, have it installed.

---

### Post by philinux on 2012-06-27
> **dino99 said:**
> The purpose of this package is for applications that only support OSS
to depend on it, hence preventing common "/dev/dsp not found" errors
that would confuse unexperienced users.


Latest update:
Mon, 05 Mar 2012 17:02:54 +0100

so you might not, like me, have it installed.

This a clean install.

```
apt-cache policy oss-compat
oss-compat:
  Installed: 1
  Candidate: 2
  Version table:
     2 0
        500 http://archive.ubuntu.com/ubuntu/ quantal/universe amd64 Packages
 *** 1 0
        100 /var/lib/dpkg/status

```

---

### Post by philinux on 2012-06-27
Found it.

[https://bugs.launchpad.net/ubuntu/+source/oss-compat/+bug/992991](https://bugs.launchpad.net/ubuntu/+source/oss-compat/+bug/992991)

---

