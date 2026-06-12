---
title: "Virtaulbox - Jaunty"
date: 2009-03-27
forum: Virtualisation
---

### Post by Mehall on 2009-03-27
I've had a few VM's working fine (my keyboard issue notwithstanding, see other thread) but when I try and use Jaunty Beta (either Gnome or KDE) I only get about a half a screen.

I can move cursor through the top to get to the bar and back down to get to the bottom bar, but it's not one full thing, the desktop is half-looped. The whole vbox window is not being utilised.

---

### Post by Perryg on 2009-03-27
> **Mehall said:**
> I've had a few VM's working fine (my keyboard issue notwithstanding, see other thread) but when I try and use Jaunty Beta (either Gnome or KDE) I only get about a half a screen.

I can move cursor through the top to get to the bar and back down to get to the bottom bar, but it's not one full thing, the desktop is half-looped. The whole vbox window is not being utilised.

There seems to be a problem with VBox and the new Xserver release read the link below.
[http://forums.virtualbox.org/viewtopic.php?f=3&t=15512#p64831](http://forums.virtualbox.org/viewtopic.php?f=3&t=15512#p64831)

I edited the install.so and it fixed it right up.  

PS you must install the guest additions from the directory where you edited the install.so file.

---

### Post by Mehall on 2009-03-27
> **Perryg said:**
> There seems to be a problem with VBox and the new Xserver release read the link below.
[http://forums.virtualbox.org/viewtopic.php?f=3&t=15512#p64831](http://forums.virtualbox.org/viewtopic.php?f=3&t=15512#p64831)

I edited the install.so and it fixed it right up.  

PS you must install the guest additions from the directory where you edited the install.so file.

cheers, I'll bear this in mind.

---

### Post by bodhi.zazen on 2009-03-28
When editing the install script, ubuntu 9.04 beta now uses version 1.7.* (and not 1.6.* as in the solutions posted for the alpha).

---

### Post by Perryg on 2009-03-31
> **bodhi.zazen said:**
> When editing the install script, ubuntu 9.04 beta now uses version 1.7.* (and not 1.6.* as in the solutions posted for the alpha).

Bodhi,

Could you elaborate a little on this for me?  My Xorg-server states 1.6.0 in Jaunty.  Are you saying that they are going to 1.7.0, and if so when?

---

### Post by bodhi.zazen on 2009-03-31
The update oh a week ago I thought showed 1.7 , I would have to check my VM later.

Adding 1.7.* to the install script definitely works.

---

### Post by Perryg on 2009-03-31
> **bodhi.zazen said:**
> The update oh a week ago I thought showed 1.7 , I would have to check my VM later.

Adding 1.7.* to the install script definitely works.

Thanks Bodhi.  
I would appreciate it if you would let me know when you have checked.  I have been watching and though Ubuntu has been doing testing with 1.7.0 I see nowhere that they are ready to release.  Of course I do not work for them so I may just be out of the loop.

---

### Post by bodhi.zazen on 2009-03-31
> **Perryg said:**
> Thanks Bodhi.  
I would appreciate it if you would let me know when you have checked.  I have been watching and though Ubuntu has been doing testing with 1.7.0 I see nowhere that they are ready to release.  Of course I do not work for them so I may just be out of the loop.

[http://packages.ubuntu.com/jaunty/xserver-xorg](http://packages.ubuntu.com/jaunty/xserver-xorg)

---

### Post by Perryg on 2009-03-31
> **bodhi.zazen said:**
> [http://packages.ubuntu.com/jaunty/xserver-xorg](http://packages.ubuntu.com/jaunty/xserver-xorg)

Thank you!

---

