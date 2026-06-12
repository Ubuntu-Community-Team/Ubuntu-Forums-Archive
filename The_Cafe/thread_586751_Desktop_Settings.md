---
title: "Desktop Settings"
date: 2007-10-22
forum: The Cafe
---

### Post by miakely on 2007-10-22
Hi guys,

I wanted to change the parameters of my 'desktop effect' through

system --> preference --> desktop effects

and I enabled some desktop effects. It did not work and now,  the toolbar
disappeared and I cannot access the terminal anymore, so that I cannot
re-initialize the desktop effects. Besides, I cannot access my home
folder, neither can I launch any applications.

Is there any way to fix it through the failsafe terminal?

Thank you so much for your (precious) help.

Kind regards,
Miakely

---

### Post by punkybouy on 2007-10-27
I found this in one of the other forums and you can edit your xorg.conf from a terminal.  Credit goes to "badlogic"

make sure that this line is in your xorg.conf


Option "AddARGBGLXVisuals" "True"

once I added that then did an alt ctrl backspace to reload it fixed it.
__________________

---

### Post by punkybouy on 2007-10-27
How about this:

#Shutdown Beryl
killall beryl-manager;
killall beryl

---

