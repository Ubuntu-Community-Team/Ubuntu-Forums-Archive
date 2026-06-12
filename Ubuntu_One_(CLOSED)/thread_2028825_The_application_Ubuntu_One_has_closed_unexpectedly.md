---
title: "The application Ubuntu One has closed unexpectedly"
date: 2012-07-18
forum: Ubuntu One (CLOSED)
---

### Post by doyleman on 2012-07-18
I have moved up to 12.04, and tried setting up ubuntu one. it crashes, says:
Depends in unknown(): ubuntuone-control-panel-common(=3.0.1-0ubuntu1) but 3.0.1-0ubuntu1 is to be installed.

---

### Post by doyleman on 2012-07-19
still no luck. the application no longer just closes unexpectedly, it just stays at the "installing" with a 100% bar, but never truly finishes.

---

### Post by doyleman on 2012-07-20
Future reference for people:
terminal:

```
sudo apt-get install ubuntuone-control-panel-qt
```

is a fix

---

