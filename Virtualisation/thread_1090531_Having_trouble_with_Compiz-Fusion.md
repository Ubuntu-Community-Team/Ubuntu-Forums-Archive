---
title: "Having trouble with Compiz-Fusion"
date: 2009-03-08
forum: Virtualisation
---

### Post by zeldarocks on 2009-03-08
I decided to install compiz fusion in an attempt to mimic a windows Vista type environment, well, the installtion went fine, but when I try to replace my vanilla (default) desktop with compiz fusion by typing 

_"compiz --replace" _

in the terminal, it gives me 

[U]"Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity"[/U]. 

 and comes back the same as it was before attempting the replacement. You guys are my last hope, I've tried tutorials and they haven't helped, please help me guys.

---

### Post by Committed on 2009-03-08
Why don't you just right click on the desktop and change the background. No need to use the terminal.

BTW,might get more response in Desktop Environments section.

---

### Post by zeldarocks on 2009-03-08
I wasn't talking about the desktop background, but the actual desktop display and effects e.i. the Compiz-Fusion environment

---

### Post by Committed on 2009-03-10
Have you installed Emerald?

in terminal type     sudo apt-get install emerald

This will install emerald theme manager.
open system/preferences/emerald theme manger
under edit themes is a theme called Oxygen 02, 
I haven't tried it but it says Vista-ish in nature.

---

### Post by UbuntuNerd on 2009-03-10
did you install any drivers because by the error it looks like is looking for the driver but didn't find it so it when back to metacity which is the default.
go to System > Administration > Hardware Drivers type in your password, the Hardware Drivers tool should show your graphic card

---

### Post by UbuntuNerd on 2009-03-10
also did you enable the effects under System > preferences > Appearance > Visual Effects and hit (Normal or Extra) to activate it.

---

