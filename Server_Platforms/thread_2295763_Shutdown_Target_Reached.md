---
title: "Shutdown Target Reached"
date: 2015-09-21
forum: Server Platforms
---

### Post by eggzenbeanz on 2015-09-21
Hi,

My 15.04 install has recently started hanging at "shutdown Target Reached" during a reboot or shutdown. It doesn't respond to any key presses. I need to physically power off the box and reboot.

Any ideas?

cheers

---

### Post by eggzenbeanz on 2015-09-22
Sorry the actual wording is "target shutdown reached" - crtl alt F1 has no effect or other key presses

---

### Post by ian-weisser on 2015-09-22
"target shutdown reached" means the system has done everything it can. The software is no longer active (halted), and it's safe for you to manually cut power. Keypresses shouldn't work - no software is listening for them.

Why has your system BIOS/EFI not picked up the final system instruction to poweroff or reboot? Sorry, I have no idea there.

---

### Post by eggzenbeanz on 2015-09-22
um thanks.

---

