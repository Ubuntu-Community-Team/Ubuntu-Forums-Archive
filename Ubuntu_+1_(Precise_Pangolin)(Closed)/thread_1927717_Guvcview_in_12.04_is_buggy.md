---
title: "Guvcview in 12.04 is buggy"
date: 2012-02-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by mörgæs on 2012-02-18
Hi, is anyone having problems with guvcview 1.5.0 in the daily build?

---

### Post by pressureman on 2012-02-18
Yep, first noticed this about a week or two ago:

```

guvcview 1.5.0
Fatal:g_thread NOT supported

```

... and then it bails out.

---

### Post by Jorge_C on 2012-02-18
Yes, there's a [bug report]("https://bugs.launchpad.net/ubuntu/+source/guvcview/+bug/901142") in Launchpad about it. Comment #4 gives a PPA with a new version where this is fixed.

---

### Post by mörgæs on 2012-02-19
> **Jorge_C said:**
> Yes, there's a [bug report]("https://bugs.launchpad.net/ubuntu/+source/guvcview/+bug/901142") in Launchpad about it. Comment #4 gives a PPA with a new version where this is fixed.

Yes, I know - I am the same Mörgæs who wrote in the bug report :-)


I was wondering if it is possible to get version 1.5.3 into 12.04, since 1.5.0 is quite buggy (or does not open at all).

---

### Post by Jorge_C on 2012-02-19
> **mörgæs said:**
> Yes, I know - I am the same Mörgæs who wrote in the bug report :-)


I was wondering if it is possible to get version 1.5.3 into 12.04, since 1.5.0 is quite buggy (or does not open at all).

Oops, I hadn't noticed that!

I certainly hope it's possible to get it in, the current version doesn't open for me either. Keeping an old version that's known to crash at startup for some users when there's a new one that fixes that doesn't look right to me, no matter what regressions it might introduce.

---

### Post by mörgæs on 2012-03-07
1.5.3 is included now, and it all seems to work well.
[https://launchpad.net/ubuntu/+source/guvcview](https://launchpad.net/ubuntu/+source/guvcview)

---

