---
title: "TESTING Backport: gdesklets 0.33.1-1ubuntu2"
date: 2005-01-12
forum: Ubuntu Backports
---

### Post by jdong on 2005-01-12
**Summary**
Community request for Gdesklets. Warty's didn't work too well?


**Backporting Process**
Grabbed + Compiled from Hoary.
Some dependency versions (with Python) couldn't be met. However, the package compiles fine with the latest Warty versions.

**Upload Log**
```

dists/warty-backports-staging/universe/binary-i386/gdesklets_0.33.1-1ubuntu2-4.10ubp1_i386.deb
      401674 100%   24.08kB/s    0:00:16  (3, 6.7% of 253)

```

**Known Issues**
None

**Testing Status**
Untested.


**NOTE**: May take a while to get on server. The upload is being shoved with UBP promotions, which will still take another 45 minutes or so to complete!

---

### Post by senectus on 2005-01-14
Is this up yet? I've updated and the version that synaptic is giving me is still the old 0.26.25ubuntu1

Should i see 0.33.1-1?

---

### Post by jdong on 2005-01-14
yuck, we need python-gnome2-extras, which seems to only be in Hoary (@ version 2.9.2). I don't want to introduce beta libraries. I'll investigate on this situation.

---

### Post by HiddenWolf on 2005-01-14
[QUOTE=jdong]yuck, we need python-gnome2-extras, which seems to only be in Hoary (@ version 2.9.2). I don't want to introduce beta libraries. I'll investigate on this situation.[/QUOTE]

Since there is nothing equivalent in warty, it wouldn't do any harm to introduce it, right?
Only desklets would try and use it.

---

### Post by rider343 on 2005-01-15
Any good news?

---

### Post by jdong on 2005-01-15
I just saved a bunch of money on my car insurance.

---

### Post by HiddenWolf on 2005-01-16
[QUOTE=jdong]I just saved a bunch of money on my car insurance.[/QUOTE]
That's good news.

---

