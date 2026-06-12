---
title: "Compiz Settings wont save."
date: 2013-04-07
forum: Ubuntu Development Version
---

### Post by Xanza on 2013-04-07
This only happens in Xubuntu 13.04 for me. This is on a fresh install after installing the latest updates.
When I launch ccsm and select the settings they work but they do not stay after a logout or reboot. Also when I relaunch ccsm the settings get reset. I tried using ccsm in root to no avail. How do I make the settings stay?

---

### Post by pnarciso on 2013-04-07
> **Xanza said:**
> This only happens in Xubuntu 13.04 for me. This is on a fresh install after installing the latest updates.
When I launch ccsm and select the settings they work but they do not stay after a logout or reboot. Also when I relaunch ccsm the settings get reset. I tried using ccsm in root to no avail. How do I make the settings stay?
It also happens in Ubuntu 13.04, the only workaround I have found is to create a startup script with options you want to make, using dconf.

---

### Post by Xanza on 2013-04-07
> **pnarciso said:**
> It also happens in Ubuntu 13.04, the only workaround I have found is to create a startup script with options you want to make, using dconf.

EDIT : Solved the problem. Compiz now saves and works even after reset
For those interested in running compiz in 13.04

Install Gconf Backend for Compiz
```
sudo apt-get install compizconfig-backend-gconf
```

Then open Compiz Config Settings Manager
Under Preferences change the backend to Gsettings Configuration Backend and make sure Intergration into the desktop environment is ticked.

Adios

---

### Post by Xanza on 2013-04-07
@pnarciso perhaps this could help you as well :)

---

### Post by ClientAlive on 2014-02-09
I came across this thread because I'm seeking a soln to this same problem. Although unity plugin is enabled, ccsm preferences do specify gconf backend and the box for desktop integration is ticked - I still experience the problem ( there has been no change ). When I make changes to settings in ccsm, in a number of places it will happen, they are not saved if I ( 1 ) hit the back button, or ( 2 ) close ccsm, or ( 3 ) restart the system. I have also tried using dconf to change some compiz settings that were problematic and they not only did not hold, but the available rows/setting that can be changed with dconf are dependent on settings specified in ccsm. For instance...

In dconf, I navigated to org > compiz > profiles > unity > plugins > core...

And the only options available to change for desktops were the ones that have something in the field at ccsm > general options > desktop size

Now, two of those fields in ccsm are empty by default; and, with ccsm not saving changes, are what is reverted to when any of ( 1 ), ( 2 ), or ( 3 ) above are carried out.

Please, does anyone have a soln? I'm finding this very frustrating at this point.

---

### Post by QDR06VV9 on 2014-02-10
> **Xanza said:**
> EDIT : Solved the problem. Compiz now saves and works even after reset
For those interested in running compiz in 13.04

Install Gconf Backend for Compiz
```
sudo apt-get install compizconfig-backend-gconf
```

Then open Compiz Config Settings Manager
Under Preferences change the backend to Gsettings Configuration Backend and make sure Intergration into the desktop environment is ticked.

Adios
Mine was a little different with Mate (works a treat by the way) I had to change "Gnome compatibility" under ccsm and then "commands Tab"
Remove everything that said gnome to mate.See Attachment

---

### Post by ClientAlive on 2014-02-10
For now, I've found other ways to accomplish what I need ( unity tweak tool and gdevilspie <-- If I can get it working properly - DOH! ). Thanks, will keep this thread in mind in case I need it.

---

