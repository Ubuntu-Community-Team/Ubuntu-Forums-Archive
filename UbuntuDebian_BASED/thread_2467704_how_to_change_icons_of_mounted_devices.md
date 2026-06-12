---
title: "how to change icons of mounted devices"
date: 2021-10-05
forum: Ubuntu/Debian BASED
---

### Post by iconoclastica2 on 2021-10-05
I am trying to distinguish legacy drive partitions from their successors by assigning a distinct icon to them. I am trying to do so by editing the mount options in gnome-disks. Here I can enter both the icon name and the symbolic icon name (the latter having no effect). My icons are stored in /usr/shared/pixmaps. I have tried both png and svg icons. I entered the full path names.

In all cases, the default icon on the file manager is changed for a grey kind of file-not-foundish image, whatever the icon file name. The effect is the same in Nautilus as in Thunar.

What am I doing wrong?

  Operating System: Zorin OS 15.3
  Kernel: Linux 5.4.0-86-generic
  Architecture: x86-64

---

### Post by iconoclastica2 on 2021-10-06
Found the answer:

[LIST]
[*]x-gvfs-icon must be one of the symbolic names listed at [https://specifications.freedesktop.org/icon-naming-spec/icon-naming-spec-latest.html](https://specifications.freedesktop.org/icon-naming-spec/icon-naming-spec-latest.html) 
[*]to add custom icons, use the command: 
[/LIST]
```

# xdg-icon-resource install --size 32 <icon path> <symbolic-name>
```

e.g.

```

# xdg-icon-resource install --size 32 /usr/share/pixmaps/hdd.png windows-disk
```

It seems that the symbolic name must have at least two parts connected by a hyphen.

---

