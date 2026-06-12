---
title: "LMMS segfault"
date: 2011-01-10
forum: Ubuntu Studio
---

### Post by ericmo on 2011-01-10
I opened LMMS 0.4.5 (the version available in lucid repo) through the terminal, and when playing a bunch of random notes on any instrument, LMMS would crash, returning "segmentation fault" in the terminal.

Luckily, this problem has been solved in LMMS 0.4.8, at least so it appears. If you're having the same problem, go to Software Sources and add:

```

deb [http://ppa.launchpad.net/tobydox/lmms/ubuntu](http://ppa.launchpad.net/tobydox/lmms/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/tobydox/lmms/ubuntu](http://ppa.launchpad.net/tobydox/lmms/ubuntu) lucid main 
```Then go to terminal and:

```
sudo aptitude reinstall lmms
```That's worked for me.

---

