---
title: "Skype update can not be installed"
date: 2007-03-05
forum: Repositories &amp; Backports
---

### Post by Yumi on 2007-03-05
Synaptics (Skype repository) offered me an update on Skype to version 1.3.0.52-2medibunt. However it does not install and comes up with "Depends on librte1 and is not installable". 

Where can I find librte1?

Michael

---

### Post by Kateikyoushi on 2007-03-05
It is in the multiverse repository. Enable it in system > administration > software sources.

---

### Post by Yumi on 2007-03-06
Thanks a lot. I did not notice that multiverse was not enabled. And I learned about System-Software Sources! Installed librte1 successful.

However, now Skype does not want to install the update anymore? Has given up or withdrawn. Anyway, I am ready when it finally comes.

Michael

---

### Post by Kateikyoushi on 2007-03-06
Try the following in terminal.

```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

