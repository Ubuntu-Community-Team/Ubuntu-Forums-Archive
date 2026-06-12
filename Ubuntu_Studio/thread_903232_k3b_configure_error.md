---
title: "k3b configure error"
date: 2008-08-28
forum: Ubuntu Studio
---

### Post by DeadCell on 2008-08-28
Googled it but no help there so i was wondering if anyone could help with fixing this error I get whilst trying to install k3b. I do ./configure and it throws this at me:
```
checking for Qt... configure: error: Qt (>= Qt 3.2 and < 4.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log 
```

What can i do?

Cheers,
//DC//

---

### Post by DeadCell on 2008-08-29
bump :(

---

### Post by Stochastic on 2008-08-30
Why not just install k3b from the repos (through synaptic)? that should fix all your Qt dependencies.

If you really need to build it from scratch then you need to download the appropriate Qt-dev library before going any further (the ones in the repos should work fine - package name: libqt4-dev).

---

