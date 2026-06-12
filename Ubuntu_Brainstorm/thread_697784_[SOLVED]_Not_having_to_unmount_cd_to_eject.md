---
title: "[SOLVED] Not having to unmount cd to eject"
date: 2008-02-15
forum: Ubuntu Brainstorm
---

### Post by alsamman on 2008-02-15
I find this feature quite annoying in ubuntu. We should have it such that when the button is pressed to eject your cd, a popup comes up instead asking "Are you sure you wish to eject?" and there is Yes, No and a checkbox that says Don't ask me again. This I find to be much better because it sure beats having to unmount just to eject. Both the unmounting and popup could exist, but the popup is just a more convenient way to eject the cd that way you dont have to unmount it yourself

---

### Post by Oldster on 2008-02-15
If you would like the eject button to work, edit /etc/sysctl.conf as root and add the following line at the bottom of the file:

```
dev.cdrom.lock=0
```

save and reboot.

---

### Post by 23meg on 2008-02-15
I haven't had to unmount to eject since Ubuntu 5.10 (Breezy). I haven't had to edit a configuration file either.

---

### Post by cszikszoy on 2008-02-15
Eject works fine without unmount for me too.

---

### Post by smartboyathome on 2008-02-16
> **cszikszoy said:**
> Eject works fine without unmount for me too.

Ditto on both my machines here as well.

---

### Post by alsamman on 2008-02-16
weird, because before Oldster told me to put in the command, it would not let me eject my cds using the button but i would have to eject it from the computer but thank you Oldster, i can now eject cds from the button

---

### Post by chrisccoulson on 2008-02-16
> **23meg said:**
> I haven't had to unmount to eject since Ubuntu 5.10 (Breezy). I haven't had to edit a configuration file either.

Neither have I.

But sometimes  I get a baloon message telling me that I removed the device without unmounting (although, the occurrence of this seems to be quite inconsistent).

---

