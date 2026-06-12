---
title: "snap-store Settings schema 'org.gnome.software' is not installed"
date: 2020-04-29
forum: Ubuntu Development Version
---

### Post by corradoventu on 2020-04-29
New install from release ISO Ubuntu 20.04 LTS "Focal Fossa" - Release amd64 (20200423)
snap store fails again.
```
corrado@corrado-x4-focal:~$ snap-store
16:44:14:0115 Gtk Failed to load module "canberra-gtk-module"
16:44:14:0116 Gtk Failed to load module "canberra-gtk-module"
16:44:14:0117 GLib-GIO Settings schema 'org.gnome.software' is not installed
Trace/breakpoint trap (core dumped)
corrado@corrado-x4-focal:~$ 
```

[https://bugs.launchpad.net/snap-store/+bug/1873388](https://bugs.launchpad.net/snap-store/+bug/1873388)
[https://forum.snapcraft.io/t/snap-store-does-not-start-again/17028](https://forum.snapcraft.io/t/snap-store-does-not-start-again/17028)

edit: solved installing a different version of snap-store. snap refresh was unsuccessful.

---

