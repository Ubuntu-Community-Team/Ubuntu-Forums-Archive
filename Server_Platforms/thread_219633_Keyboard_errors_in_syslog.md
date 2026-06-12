---
title: "Keyboard errors in syslog"
date: 2006-07-20
forum: Server Platforms
---

### Post by osaeris on 2006-07-20
We have an Ubuntu Breezy headless server in our comms room.

I regularly tail the syslog via ssh to check for errors and found that there were hundreds of entries like this:

Jul 20 14:41:14 localhost kernel: [3117344.316520] atkbd.c: Keyboard on isa0060/serio0 reports too many keys pressed.

After Googling around and finding nothing I realised there was probably a simpler solution: remove the pile of books someone left on top of the keyboard.

Good grief.

---

