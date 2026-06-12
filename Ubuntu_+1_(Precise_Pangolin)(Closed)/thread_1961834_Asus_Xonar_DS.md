---
title: "Asus Xonar DS"
date: 2012-04-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by expatCM on 2012-04-19
Any suggestions of how to install this sound card with 12.04?

The card sort of works with left and right channels but nothing else (no woofer, no rear).  The volume control is very limited.   The card did work perfectly with 10.10.

I see that others are trying to report this as a bug but for some reason you have to report bugs as application errors and this looks like a driver challenge.

So any ideas what to do other than wait for an automagical update hopefully in the near future?

---

### Post by tominglis on 2012-04-20
I reported this as a bug for precise. My analogue output has actually disappeared from the sound indicator. Everything is there in alsamixer though, but presumably I would need to bypass pulseaudio to make it work?

---

### Post by cariboo on 2012-04-20
> **expatCM said:**
> Any suggestions of how to install this sound card with 12.04?

The card sort of works with left and right channels but nothing else (no woofer, no rear).  The volume control is very limited.   The card did work perfectly with 10.10.

I see that others are trying to report this as a bug but for some reason you have to report bugs as application errors and this looks like a driver challenge.

So any ideas what to do other than wait for an automagical update hopefully in the near future?

If you want to create a bug report about a driver problem, report the bug against the kernel:

```
sudo ubuntu-bug linux
```

---

