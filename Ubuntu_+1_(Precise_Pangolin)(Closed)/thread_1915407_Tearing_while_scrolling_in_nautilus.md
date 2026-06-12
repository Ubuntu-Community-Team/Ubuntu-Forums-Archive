---
title: "Tearing while scrolling in nautilus"
date: 2012-01-26
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by InphekD on 2012-01-26
Tearing happens while scrolling in nautilus.

Steps to reproduce:
- View mode: list; (no tearing when other two modes are selected)
- Mouse pointer has to be inside nautilus;
- Scroll with mouse wheel (if you scroll slowly - you wont see the tearing);

Tested on 12.04 x64 and 11.10 x64. Default settings. OSS AMD drivers. Video graphics is ATI 3650m.

Can anyone reproduce this? Is it a bug?

---

### Post by lucazade on 2012-01-26
not a news for me.. I clearly see this weird issue in GTKTreeView widget in every release of GTK/GNOME.

[http://developer.gnome.org/gtk/2.24/GtkTreeView.html](http://developer.gnome.org/gtk/2.24/GtkTreeView.html)

and I don't expect this to be solved any time soon.

This is one of the reasons why QT4 are far far better than GTK.

---

