---
title: "Ubuntu 9.10 wine Repository"
date: 2009-12-02
forum: Wine
---

### Post by Liolikas on 2009-12-02
I try to add wine Repository:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
And when I try apt-get update:
```

...
...
W: GPG error: http://ppa.launchpad.net karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

```
I really added Scott Ritchie's key.

What is wrong!?

---

### Post by 8Kuula on 2009-12-02
sudo add-apt-repository ppa:ubuntu-wine/ppa
Adds key too.

---

### Post by Predrag on 2009-12-02
I think that you will not be able to install wine because there is some bug

---

### Post by Rody on 2009-12-02
+1

> **8kuula said:**
> sudo add-apt-repository ppa:ubuntu-wine/ppa
adds key too.

---

### Post by tulcak on 2009-12-04
seriously, does ANYTHING run in Wine?  I've yet to get anything at all to run using wine.

---

### Post by BAMF1501 on 2009-12-04
Yes stuff runs under wine i got mw2 cod4 etc tons of games

---

### Post by Liolikas on 2009-12-04
Thanks for answers. So many things, old ways are outdated nowadays...

---

### Post by hikaricore on 2009-12-04
> **Predrag said:**
> I think that you will not be able to install wine because there is some bug

please don't post garbage like this.

> **tulcak said:**
> seriously, does ANYTHING run in Wine?  I've yet to get anything at all to run using wine.

plenty of things run under wine, it's best to check the stickies and the appdb instead of wasting time with things that do not run

---

