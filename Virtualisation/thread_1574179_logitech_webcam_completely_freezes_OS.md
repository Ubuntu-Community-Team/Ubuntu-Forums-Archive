---
title: "logitech webcam completely freezes OS"
date: 2010-09-13
forum: Virtualisation
---

### Post by Jacksoniii on 2010-09-13
ok so my logitech webcam 9000 pro works fine on ubuntu 10.04, well atleast for skype.. but when i enable the webcam for VMware player running virtual xp pro, the whole system freezes.. i tried running the driver package and waiting for it to tell me when to plug it in.. still when i plug it in the whole system freezes... can someone help?

---

### Post by mutifo on 2010-11-21
Did you managed to resolve this issue ?

I've got the same problem with C310 webcam and Ubuntu 10.10 64bit. Guest OS doesn't matter. It can be even linux livecd during the boot. If I connect webcam to the guest - whole system freezes.
Maybe the problem is that webcam is somehow recognized as keyboard ?

```
[   799.554] (II) config/udev: Adding input device UVC Camera (046d:081b) (/dev/input/event13)
[   799.554] (**) UVC Camera (046d:081b): Applying InputClass "evdev keyboard catchall"
[   799.554] (**) UVC Camera (046d:081b): always reports core events
[   799.554] (**) UVC Camera (046d:081b): Device: "/dev/input/event13"
[   799.592] (II) UVC Camera (046d:081b): Found keys
[   799.592] (II) UVC Camera (046d:081b): Configuring as keyboard
[   799.593] (II) XINPUT: Adding extended input device "UVC Camera (046d:081b)" (type: KEYBOARD)
[   799.593] (**) Option "xkb_rules" "evdev"
[   799.593] (**) Option "xkb_model" "pc105"
[   799.593] (**) Option "xkb_layout" "pl"
[   799.593] (**) Option "xkb_options" "lv3:ralt_switch"

```

---

### Post by b0b138 on 2010-11-25
I am also having this problem. Whats really bad is it used to work but stopped suddenly

---

