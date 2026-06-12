---
title: "Suspend not working"
date: 2009-07-07
forum: System76 Support
---

### Post by biologic on 2009-07-07
When I close the lid on my Starling, or go to Quit -> Suspend, the screen immediately disappears but comes back a second later with a black background and a single text blinking underscore _ in the upper left hand corner. The fans stay on, the display stays on, and it remains warm to the touch, i.e., not suspended. Nothing I do can bring it back until I power cycle the machine.

---

### Post by biologic on 2009-07-07
Further testing shows that this behaviour also occurs when using Hibernate from the Quit menu.

---

### Post by thomasaaron on 2009-07-08
Run your System76 Driver.
Reboot.
Then try suspend.

---

### Post by biologic on 2009-07-08
I ran 'install' on the Driver tab of the System76 Driver program. I assume that's what you meant by 'run the driver'. The behavior remained the same, and suspend/hibernate required a power cycle to recover.

I then ran 'Restore' from the 'Restore System' tab of the System76 Driver program, which you could have also meant by 'run the driver'. After another reboot, the behavior is still the same.

---

### Post by thomasaaron on 2009-07-08
OK. Please bump this tomorrow and I'll run some tests.

---

### Post by biologic on 2009-07-09
Bump.

---

### Post by biologic on 2009-07-10
This problem was resolved by the same thing that fixed my kernel problems (generating a completely new menu.lst): [http://ubuntuforums.org/showthread.php?t=1206110](http://ubuntuforums.org/showthread.php?t=1206110)

Diffing the menu.lst files, it appears that the culprit was appending pciehp.pciehp_force=1 to the kernel. I had been getting an error regarding pciehp on bootup, and that is also gone now.

---

### Post by thomasaaron on 2009-07-10
D'oh!

Just finished testing our shop Starling and it suspended fine. Didn't realize you had posted both threads. Sorry I didn't catch that.

---

