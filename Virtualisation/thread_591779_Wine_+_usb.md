---
title: "Wine + usb?"
date: 2007-10-25
forum: Virtualisation
---

### Post by pointyblue on 2007-10-25
Do any of you know if it possible to enable USB-support in Wine?

I need to sync my gps but it's not linux compatible and Wine can't find it.

:confused:

---

### Post by rdoolen on 2007-10-25
I heard you can make a symlink to your USB, it should be something like /dev/tty0usb or something kinda close to that. Call it comX where X is a number and put it in the dosdevices directory in the wine created "windows" directory. Sorry that these directions are so vague, its all from memory and its been awhile.

Oh yeah, I never got it to work completely. I could see the device and even get the serial number from it. But, I could never get any actaul data from it.

Good luck, if you are successful post it here, I'd love to hear the solution.

---

