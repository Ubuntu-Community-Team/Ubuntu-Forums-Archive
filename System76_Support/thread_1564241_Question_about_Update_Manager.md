---
title: "Question about Update Manager"
date: 2010-08-30
forum: System76 Support
---

### Post by black_ice=cream on 2010-08-30
So whenever I install the updates, there are three that never seem to work. I want to get rid of them, but I don't know how. ???

---

### Post by Vrekk on 2010-08-30
Try it with ```
sudo apt-get update && sudo apt-get upgrade
```
It should tell you which three were not updated, and then just run ```
sudo apt-get install package1 package2 package3
```

---

### Post by black_ice=cream on 2010-08-30
Thanks that worked

---

