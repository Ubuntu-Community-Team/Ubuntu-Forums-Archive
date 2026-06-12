---
title: "Windows 7 inside Ubuntu 9.10"
date: 2010-01-28
forum: Virtualisation
---

### Post by Jackzor on 2010-01-28
Okay, I am wanted to try to fix a few things with my Virtual Windows 7.

First and formost. I want my resolution set to 1280x800 It doesn't offer that.

Second I want areo to work.

Thrid I want to know if it is possible to run Windows on ONE desktop full screen and be able to switch desktops back to ubuntu.

Also.. My sound isn't working in windows?



Btw I have the SAME copy installed on a partition for a dualboot.
And everything works perfect.

---

### Post by drdanielfc on 2010-01-28
> **Jackzor said:**
> Okay, I am wanted to try to fix a few things with my Virtual Windows 7.

First and formost. I want my resolution set to 1280x800 It doesn't offer that.

Second I want areo to work.

Thrid I want to know if it is possible to run Windows on ONE desktop full screen and be able to switch desktops back to ubuntu.

Also.. My sound isn't working in windows?



Btw I have the SAME copy installed on a partition for a dualboot.
And everything works perfect.

I'm using vbox (the binary, not OSE), and only with xp but for xp i can tell you this:

1. Make sure you hve the virtualbox tools installed, it will adjust the resolution for you (very nicely, it even adjusts it to make it fit the window when in windowed mode)
2. you'll have to get 2d acceleration to work in ubuntu and then change the setting in your display section of the virtual machine (i havnt been successful in this)
3. completely possible. hit your host key (usually the right ctrl) once to lose keyboard focus, and then use your ctr+alt+left/right to switch workspaces
4. VBOX TOOLS!

edit: sorry if you didnt know how to go fullscreen, its host+f and i suggest using seamless mode (very kool - host+l i think)

---

### Post by Jackzor on 2010-01-30
Yeah I installed it and I have done it all before with XP it was amazing. But. With this it WAS at 1280x699? Lol, And I changed it to 1024x768 And its stuck. I can't put it at 1280x800 like it should be?

---

### Post by Jackzor on 2010-01-31
Right ctrl+g fixed resolution.

Now all I want is a way to make windows start up on boot. AND it to start on a different Desktop

---

### Post by drdanielfc on 2010-02-02
> **Jackzor said:**
> Right ctrl+g fixed resolution.

Now all I want is a way to make windows start up on boot. AND it to start on a different Desktop

The "startup applications" should help you there, im sure you could google something similar. If you need some help ill see what i can do

---

