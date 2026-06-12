---
title: "Can't boot after tweaking login logo"
date: 2013-07-02
forum: Ubuntu Studio
---

### Post by nesskillerofgiygas on 2013-07-02
I edited the login logo for an Ubuntu Studio-injected Ubuntu installation (sudo apt-get install ubuntustudio-desktop). The login screen, however, looked vanilla. However, after it didn't show up, I restarted to find that it woudn't even go past the splash screen. Is there any way to fix this?


note: I did try to reinstall Ubuntu via live CD, but it didn't even go past the splash screen there.

note 2: I CAN use a work-around to get to the TTY terminals (going to failsafeX in recovery mode returns cannot stat /etc/x11/x, which I then cancel with ^C. This lets it boot to no-GUI mode)

---

### Post by Bucky Ball on 2013-07-02
Welcome to the forums.

Have you tried 'startx' in a terminal? Ubuntu Studio uses Xfce rather than Unity so there could be some kind of conflict there. Strange you can't boot from the CD though. I am confused about this, though.

> The login screen, however, looked vanilla. However, after it didn't show up, I restarted to find that it woudn't even go past the splash screen.

The login screen looked vanilla then didn't show up on a reboot? Can you be more specific about what is happening and error messages, if any, you are getting?

---

