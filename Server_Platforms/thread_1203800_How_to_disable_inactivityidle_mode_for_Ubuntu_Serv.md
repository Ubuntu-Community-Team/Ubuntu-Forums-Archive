---
title: "How to disable inactivity/idle mode for Ubuntu Server"
date: 2009-07-03
forum: Server Platforms
---

### Post by ndxtg on 2009-07-03
For some reasons: I installed Xorg 11 and OpenBox on Ubuntu Jaunty (Server). After a period of time (>3hours), with no mouse and keyboard activity, all the programs (which are running on OpenBox) are freeze. 

The screen still displays the programs but they don't work at all. For example: the flash content in firefox freezes, the movie player freezes. etc. 

I even used xmacro in the background to simulate mouse movements every 30mins to make the system think the mouse is not inactive, but it also freeze xmacro. When I mean freeze, it means the screen is paused (same as how you paused a dvd movie).

I already disabled the screen saver and dpms (using xset), so they are not the reasons. When the "freeze thing" happens which is >3 hours after inactivity, the screen is still on and I can see it so that means the screensaver and turnoff screen were completely disabled. :popcorn:


It stops pausing right after any key press or mouse movement. Could anyone help me how to fix it? I reckon this issue is caused by:

_a feature in Ubuntu that change the server to idle mode after mouse/keyboard inactivity. This idle mode may turn off the hdd/cpu/screen and freeze the system or sort of to minimize the power consumption. If this is the case, how to disable this feature? 

_or maybe by Xorg or Openbox. In this case, could anyone tell me where to config it? (I've looked for 2 days over Google and this forum but no luck)

I really appreciate. Thank you very much. (this is my first post even though I joined the forum last year) :lolflag:

---

### Post by ndxtg on 2009-07-04
problem solve! install gnome-core and gnome-power-manager
do not use openbox

---

### Post by dragos2 on 2009-07-05
Thanks. I was looking for this. I was having an similary behaviour through NX sessions
usgin gnome-core and gdm.

Although I have not tested it yet diasbling ACPI should fix this too.

---

