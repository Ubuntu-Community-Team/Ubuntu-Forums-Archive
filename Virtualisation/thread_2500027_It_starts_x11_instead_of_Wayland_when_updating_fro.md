---
title: "It starts x11 instead of Wayland when updating from 6.5 &gt; 6.8"
date: 2024-08-19
forum: Virtualisation
---

### Post by ubcandles49 on 2024-08-19
I updated the kernel on my libvirt/qemu 22.04 VM.  It seem to select X11 from the start like you can see in the logs below. I can't find any error related to Wayland in the gnome logs. Wayland works when I boot the 6.5.0~45 kernel. I want to use Wayland. How to fix this or find the issue?
```
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmDisplay: seat id: seat0
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmDisplay: supported session types: x11
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmDisplay: session type: x11
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmDisplay: supported session types: (null)
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmDisplay: local: yes
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmDisplay: allow timed login: yes
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmDisplay: initial: no
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmDisplay: session class: greeter
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmDisplay: seat id: (null)
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmDisplay: id: (null)
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmLocalDisplayFactory: Adding display on seat seat0
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmLocalDisplayFactory: x11 login display for seat seat0 requested
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmLocalDisplayFactory: New displays on seat0 will use x11
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmLocalDisplayFactory: Getting session type (prefers xorg, falling back: no)
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmLocalDisplayFactory: System supports graphics
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmLocalDisplayFactory: udev has settled enough for graphics.
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmLocalDisplayFactory: Found primary PCI graphics adapter, proceeding.
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmLocalDisplayFactory: Checking if udev has settled enough to support graphics.
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmLocalDisplayFactory: enumerating seats from logind
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: GdmManager: GDM starting to manage displays
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: Successfully connected to D-Bus
Aug 19 13:16:48 hostname systemd[1]: Started GNOME Display Manager.
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: Changing user:group to gdm:gdm
Aug 19 13:16:48 hostname gdm3[1739]: Gdm: Enabling debugging
Aug 19 13:16:48 hostname systemd[1]: Starting GNOME Display Manager...
```

EDIT:
Wayland works with QXL. Not with Virtio

---

