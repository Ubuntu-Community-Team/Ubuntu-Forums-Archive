---
title: "Can't update to 1.2"
date: 2010-07-30
forum: Wine
---

### Post by IvoP123 on 2010-07-30
I had wine 1.1.28 and since than i can't update to 1.2. I uninstalled the 1.1.28 version and added *ppa:ubuntu-wine/ppa *but whenever i try to install new version it still says 1.1.28 in the winecfg. I tried to delete .wine folder too but that didn't help either. What should i do? :(

I uninstalled it from synaptic and deleted .wine folder as i sayed previously but when i type wine --version in terminal it still says 1.1.28 :S

---

### Post by kostkon on 2010-07-30
You could open a terminal, give:
```
apt-cache policy wine1.2
```
and post the output here.

---

