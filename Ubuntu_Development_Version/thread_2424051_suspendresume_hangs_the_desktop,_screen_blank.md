---
title: "suspend/resume hangs the desktop, screen blank"
date: 2019-08-02
forum: Ubuntu Development Version
---

### Post by Vasu_Muppalla on 2019-08-02
On stock ubuntu daily build with latest updates as of today, suspend/resume returns blank screen, no response. Need a hard reset with power button.

H/w is Huawei matebook D with ryzen 2500U.

I do see firmware missing for raven messages.

---

### Post by Vasu_Muppalla on 2019-08-08
solved- I use iommu=soft as kernel boot param. Also had to remove the "help" app from favorites- that was causing mouse cursor to disappear after resume. It was also throwing errors.

---

