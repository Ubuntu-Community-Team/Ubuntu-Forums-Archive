---
title: "emulate a virtual desktop problem"
date: 2009-05-06
forum: Wine
---

### Post by zero777zero on 2009-05-06
when i uncheck this option and close down wine it comes back up with the virtual desktop still checked! this srsly sucks and i don't want to uninstall wine cuz i have a lot of windows progs installed

ver 1.1.20

---

### Post by zero777zero on 2009-05-06
looks like the emulator is cutting off the bottom of the wine window so i cant save, how annoying

[IMG]http://img25.imageshack.us/img25/8472/screenshotyoj.png[/IMG]

of course maximizing the wine window doesnt help since the emulated area doesnt change

---

### Post by NightMKoder on 2009-05-06
try tabbing through the buttons. In the worst case, you can do

```

wine explorer /desktop=a,1024x768 winecfg

```

---

