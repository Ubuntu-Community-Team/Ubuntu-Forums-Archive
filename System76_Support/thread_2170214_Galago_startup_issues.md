---
title: "Galago startup issues"
date: 2013-08-25
forum: System76 Support
---

### Post by nkasprak on 2013-08-25
Occasionally (maybe 40-50% of the time) I'll boot up my new Galago and instead of being taken to the log in screen, all I see is a black screen with a blinking underscore, and a mouse pointer over it. I can switch to a text terminal using ctrl-alt-f1. I then try to start the display manager manually by typing sudo lightdm start, and when I do this I get taken back to the black screen with the blinking underscore and the mouse pointer. If I switch back to the terminal I was in, I see an error message: 

"Failed to use bus name org.freedesktop.DisplayManager, do you have appropriate permissions?"

I get the same message if I try lightdm stop, lightdm restart, sudo, no sudo (in which case I just get the message that lightdm must be run as root), whatever - nothing seems to work. Only solution is to reboot and hope that the display manager starts successfully.

Any ideas?

---

### Post by isantop on 2013-08-26
Please see this post: [http://ubuntuforums.org/showthread.php?t=2170537](http://ubuntuforums.org/showthread.php?t=2170537)

We just released a fix to this issue in our System76 PPA.

---

### Post by nkasprak on 2013-08-27
Great, thanks. Fix appears to have worked.

---

