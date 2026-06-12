---
title: "Indicator-multiload, weird network behaviour."
date: 2012-06-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by philinux on 2012-06-13
See attached screenshot. It's showing net in continuous use up and down. Whereas system monitor itself shows no activity. Wireless light on laptop shows no activity either.

I'll bug this if someone sees the same.

---

### Post by dino99 on 2012-06-13
wow, big pipe :popcorn:

---

### Post by philinux on 2012-06-13
> **dino99 said:**
> wow, big pipe :popcorn:

Indeed.

I just got conky going and it's showing 1 GiB/s up and down so it must be network manager or other reporting wrongly.

[edit] Well a reboot sorted that out but it came back after a few minutes.

---

### Post by fjgaude on 2012-06-13
> **philinux said:**
> Indeed.

I just got conky going and it's showing 1 GiB/s up and down so it must be network manager or other reporting wrongly.

[edit] Well a reboot sorted that out but it came back after a few minutes.

No issues here on my Dell mini-10... all indicators are normal including Net up/down.

---

### Post by philinux on 2012-06-20
Still got this. Bugged it.

[https://bugs.launchpad.net/ubuntu/+source/indicator-multiload/+bug/1015623](https://bugs.launchpad.net/ubuntu/+source/indicator-multiload/+bug/1015623)

---

