---
title: "Screen not coming back after suspend"
date: 2013-02-25
forum: Ubuntu Development Version
---

### Post by superchar42 on 2013-02-25
This has happened twice now (glad I saved my work!) - what program would be what I report using the ubuntu-bug utility?

---

### Post by lucazade on 2013-02-26
I'd file the bug via:
```
ubuntu-bug pm-utils
```

by the way on my netbook I have to remove video quirks to make suspend working:
```
sudo mv /usr/lib/pm-utils/sleep.d/99video /usr/lib/pm-utils/99video
```

---

