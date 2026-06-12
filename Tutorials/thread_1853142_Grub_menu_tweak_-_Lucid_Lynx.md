---
title: "Grub menu tweak - Lucid Lynx"
date: 2011-10-01
forum: Tutorials
---

### Post by serial# on 2011-10-01
How to change the color of your boot menu. I'm running 10.04 but this may work for the newer versions and possibly the older ones.

Make a backup of the orginal:
```

sudo cp /boot/grub/grub.cfg /boot/grub/grub.cfg-backup

```Now open the orignal:
```

sudo gedit /boot/grub/grub.cfg

```Now scroll down or search for the following:
```

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=white/light-grey
### END /etc/grub.d/05_debian_theme ###

```You can change the colors to whatever you like an example of mine:
```

set menu_color_normal=black/green
set menu_color_highlight=red/blue

```

---

