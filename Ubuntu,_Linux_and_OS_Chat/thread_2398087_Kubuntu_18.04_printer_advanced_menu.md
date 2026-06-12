---
title: "Kubuntu 18.04 printer advanced menu"
date: 2018-08-07
forum: Ubuntu, Linux and OS Chat
---

### Post by vansven on 2018-08-07
In Kubuntu 16.04, when printing from e.g. Okular, I have for the printer under "Properties" the menues "Page" and "Advanced" - in the "Advanced" menu I'm able to set options for the printer driver, e.g. color printing.

However, in Kubuntu 18.04 I have for the same printer under "Properties" the menues "Page" and "Job Options", but in "Job Options" I'm not able to set options for the printer driver. Where can I find the content of the "Advanced" menu in Kubuntu 18.04 that I have in Kubuntu 16.04?

Thanks / Van

---

### Post by vansven on 2018-08-12
The problem seems to be that Okular uses Qt for printing and the  Qt-version used in Kubuntu 18.04 is not able to show the advanced CUPS  options. That's sad because it was possible in the Qt-version used in  Kubuntu 16.04. In recent versions of Qt it seems to have been fixed, see [https://www.kdab.com/better-support-for-cups-features-in-qt-5-11/](https://www.kdab.com/better-support-for-cups-features-in-qt-5-11/). I really would like to get a patch for my Kubuntu 18.04 installation to enable the advanced menu.

---

### Post by coffeecat on 2018-08-12
[Duplicate](https://ubuntuforums.org/showthread.php?t=2398295). Thread closed.

Please do no post duplicates. This dilutes community effort and causes confusion. Also, this sub-forum is for chat, not technical support.

---

