---
title: "Can't remove on-screen keyboard when booting into Saucy"
date: 2013-10-03
forum: Ubuntu Development Version
---

### Post by volkerbradley on 2013-10-03
Can you help me remove the keyboard on the screen that I when booting into 13.10?
I have read lots of posts about this but the solutions all seem to be related to seeing the keyboard when logging out and logging back in.  These solutions don't work. The keyboard shows up again when I completely shut the computer down and then boot up again.
Clicking on the X's on the keyboard does not remove it.

---

### Post by philinux on 2013-10-03
Moved to ubuntu+1 forum,

Have you installed onboard? 

Is this what you are seeing. [https://apps.ubuntu.com/cat/applications/raring/onboard/](https://apps.ubuntu.com/cat/applications/raring/onboard/)

---

### Post by grahammechanical on 2013-10-03
I have not tested this for a long time but I think the solution in 13.10 is the same as in 13.04 and the other versions of Ubuntu and it is at the top of the login screen. There we have an option to show an on screen keyboard. Once we set it to enabled then it will always appear until we disable it at the login screen. This function is part of the Universal Access options of Ubuntu. We will find a slider to switch the On Screen keyboard On and Off in System Settings>Universal Access. Either should work. If they do not then please file a bug report.

Regards.

---

### Post by philinux on 2013-10-03
> **grahammechanical said:**
> I have not tested this for a long time but I think the solution in 13.10 is the same as in 13.04 and the other versions of Ubuntu and it is at the top of the login screen. There we have an option to show an on screen keyboard. Once we set it to enabled then it will always appear until we disable it at the login screen. This function is part of the Universal Access options of Ubuntu. We will find a slider to switch the On Screen keyboard On and Off in System Settings>Universal Access. Either should work. If they do not then please file a bug report.

Regards.

+1.  I forgot onboard is installed in the default setup.

---

### Post by volkerbradley on 2013-10-03
> **grahammechanical said:**
> I have not tested this for a long time but I think the solution in 13.10 is the same as in 13.04 and the other versions of Ubuntu and it is at the top of the login screen. There we have an option to show an on screen keyboard. Once we set it to enabled then it will always appear until we disable it at the login screen. This function is part of the Universal Access options of Ubuntu. We will find a slider to switch the On Screen keyboard On and Off in System Settings>Universal Access. Either should work. If they do not then please file a bug report.

Regards.
Thanks for pointing me in the right direction.  That fixed the problem.
I had clicked on the keyboard icon and did not find the choice to remove the keyboard.  Instead the choice to remove the keyboard is under the small icon that looks like a person.

---

