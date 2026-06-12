---
title: "VirtualBox: How to make your keyboard work again"
date: 2010-09-13
forum: Virtualisation
---

### Post by locoHost on 2010-09-13
This just an FYI for a trick I stumbled upon. In VBox 3.2.8 when the screen saver kicks in or maybe it's display sleep, not sure exactly when it happens, the keyboard stops responding. Real fun :-/ I discovered that if you just select "Session Info" from the VBox "Machine" menu, then close the "Session Info" window, the keyboard starts working again! So wierd. Maybe someone here can explain what's going on.

Anyway, I just wanted to share in case the dead VBox keyboard was bugging you too :-)

---

### Post by quixote on 2010-09-15
Hey, thanks for that!  I've been having to just close the whole vm, which is a major pain.  

The most recent vbox is fast and nice and all, but it sure seems buggy.  There's this keyboard nonsense, and then I just *cannot* get guest additions to work for a linux guest on a linux host.  (WinXP guest does work.)  Oracle sure slapped their logo on fast, but they don't seem to be doing anything which is any use.

---

### Post by MauriceH2O on 2010-11-06
I have been able to get the keyboard to start working again after screen saver by hitting ctrl-alt-delete and then clicking the cancel option. Then the keyboard will start responding and I can enter a password.

---

### Post by pizzacake on 2011-05-12
> **MauriceH2O said:**
> I have been able to get the keyboard to start working again after screen saver by hitting ctrl-alt-delete and then clicking the cancel option. Then the keyboard will start responding and I can enter a password.

Thanks, it worked!:)

I'm using VirtualBox 4 to run Windows on Mac OS X.  When my MacBook wakes from sleep and I try to type in Virtualbox it is like I have a modifier key pressed.  I would have to restart Virtualbox, but now I just hit ctrl-alt-delete (fn-backspace for those without a delete key) which brings up the task manager, close it and the keys are working as normal.

---

