---
title: "qemu | kvm resolution"
date: 2010-12-26
forum: Virtualisation
---

### Post by n~kf)}BW% on 2010-12-26
Hello,

If i start Ubuntu LiveCD virtually, the resolution is horribly low. How could i possibly change this via qemu or kvm? Changing the resolution in grub is not too welcome, but i'll do it if it's the only solution.

Best regards.

---

### Post by bodhi.zazen on 2010-12-26
You can try the "std" video driver, it is often times very slow.

See: [http://blog.bodhizazen.net/linux/how-to-improve-resolution-in-kvm/](http://blog.bodhizazen.net/linux/how-to-improve-resolution-in-kvm/)

Or you can run your guests without X and connect via the built in vnc viewer.

---

