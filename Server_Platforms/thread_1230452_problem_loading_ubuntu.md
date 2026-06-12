---
title: "problem loading ubuntu"
date: 2009-08-03
forum: Server Platforms
---

### Post by Cyber Spot on 2009-08-03
problem

kinit: No resume image, doing normal boot...

We think it has something to do with the nvidia video graphics.
We do not want to re-install ubuntu in order to save some documents in the computer.

Thanks

CS

---

### Post by wojox on 2009-08-03
Run this:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by drs305 on 2009-08-03
The message is telling you that during the boot process no hibernate image was found and that it is going to continue the normal boot process. If your system is booting normally, it isn't an error and nothing connected with this message is wrong with your system (unless you tried to hibernate your system I suppose ;-) ).

---

### Post by steveneddy on 2009-08-03
> **drs305 said:**
> The message is telling you that during the boot process no hibernate image was found and that it is going to continue the normal boot process. If your system is booting normally, it isn't an error and nothing connected with this message is wrong with your system (unless you tried to hibernate your system I suppose ;-) ).

That is true, but I am having this same issue after a failed kernel and nvidia driver install.

Only boots into a low resolution and only get correct resolution after removal of all nvidia drivers and kernel modules and remove nvidia reference from xorg.conf.

Maybe I need to post a thread.

---

