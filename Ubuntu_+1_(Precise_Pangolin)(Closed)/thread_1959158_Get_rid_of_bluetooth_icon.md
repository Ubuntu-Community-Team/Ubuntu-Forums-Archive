---
title: "Get rid of bluetooth icon?"
date: 2012-04-15
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by josephellengar on 2012-04-15
Hi. I just upgraded to 12.04, and suddenly my long-functioning system tray is messed up. There is a large, ugly bluetooth icon sitting there. I used to be able to uncheck a box in bluetooth options to get rid of it, but that option is no longer available, and if I remove the gnome-bluetooth package, I also lose gnome-tweak-tool. Is there any other way to get rid of this now?

Thanks!

(Crossposted from absolute beginner; decided it fit better here)

---

### Post by jbicha on 2012-04-15
Install dconf-tools. Open dconf-editor. Navigate to com.canonical.indicator.bluetooth and uncheck the visible option.

---

### Post by josephellengar on 2012-04-15
> **jbicha said:**
> Install dconf-tools. Open dconf-editor. Navigate to com.canonical.indicator.bluetooth and uncheck the visible option.

Worked. Thanks!

---

