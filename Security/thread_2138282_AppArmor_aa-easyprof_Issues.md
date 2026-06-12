---
title: "AppArmor aa-easyprof Issues"
date: 2013-04-23
forum: Security
---

### Post by SoronZero on 2013-04-23
I have an a couple of issues with aa-easyprof, specifically if I use a path with a space in it, even though it is escaped with a \ I get the following error

```

Traceback (most recent call last):
File "/usr/bin/aa-easyprof", line 63, in <module>
p = easyp.gen_policy(**params)
File "/usr/lib/python3/dist-packages/apparmor/easyprof.py", line 446, in gen_policy
raise AppArmorException("Invalid policy")

```

I am specifically passing it "--read-path=$BASEPATH/Save\ States/" (its in a quick script I wrote for various emulators) and everything else passed without a space in the path gets generated ok.

The second issue I have with aa-easyprof is that the man documentation is incorrect in that it specifies --write-dir=, when in in fact it is --write-path= , but not a biggie, is there something I am missing aa-easyprof to pass paths with a space in them or is this a bug?

---

