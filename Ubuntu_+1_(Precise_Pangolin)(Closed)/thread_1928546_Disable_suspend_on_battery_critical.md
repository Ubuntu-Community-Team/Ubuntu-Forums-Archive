---
title: "Disable suspend on battery critical?"
date: 2012-02-20
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by BeRoot ReBoot on 2012-02-20
When has this option been removed? My laptop battery sensor is broken and reports an empty battery all the time, and there's no option to disable this behaviour in 12.04. Why would you even remove that? Also, the gnome-power-manager entry is gone even from gconf-editor, so there's no way of putting this back in? What the heck, canonical?

---

### Post by jbicha on 2012-02-20
Canonical had nothing to do with this.

What you probably want is dconf-editor (install dconf-tools to get it). And then navigate to org.gnome.settings-daemon.plugins.power and then set critical-battery-action to nothing.

---

