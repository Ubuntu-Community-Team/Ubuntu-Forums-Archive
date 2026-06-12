---
title: "How to remove Wine completely?"
date: 2011-01-08
forum: Wine
---

### Post by Its_Rishi on 2011-01-08
After wine installed it makes "add new application" list worst with windows media player & Run DLL, So i need to remove all of its files completely and permanently from ubuntu.

---

### Post by dino99 on 2011-01-08
open synaptic (system admin synaptic) and select wine & winetricks for complete removal (right click)

then into your /home, delete .wine folder (ctrl+h to unhide it)

---

### Post by Suroh66 on 2011-01-08
Another way is by going to your terminal and entering sudo apt-get purge wine.xx xx being the number 1.2 Etc if your using wine 1.3 beta you do the same thing but replace the purge with remove. Open the terminal again and enter rm -r .wine which would remove it entirely

---

### Post by Bucky Ball on 2011-01-08
> **Suroh66 said:**
> Another way is by going to your terminal and entering sudo apt-get purge wine.xx xx being the number 1.2 Etc if your using wine 1.3 beta you do the same thing but replace the purge with remove. Open the terminal again and enter rm -r .wine which would remove it entirely

The age old question: how to remove Wine entirely. I think you'll find it is impossible to remove entirely (like most things associated with Windows). If you have installed any Windows programs with wine you need to remove them first so Wine is 'empty' or it won't budge.

Suroh66, if you have removed Wine, open a terminal and type 'locate wine'. See anything?

If you remove as suggested anything left will just sit there doing nothing, so no biggie. Just annoying. Doesn't effect the system. ;)

---

### Post by Suroh66 on 2011-01-08
Bucky Ball yes I realize you need to remove the installed programs first but one would guess and or hope most people who know to do that first. I was simply sugesting another way to remove wine :)

---

### Post by Bucky Ball on 2011-01-08
> **Suroh66 said:**
> Bucky Ball yes I realize you need to remove the installed programs first but one would guess and or hope most people who know to do that first. I was simply sugesting another way to remove wine :)

New user; never assume. I know you were suggesting another way to remove it and good. I'm suggesting that getting rid of *ALL* wine flotsam is nigh on impossible. No offence meant so don't take any. ;)

---

### Post by Suroh66 on 2011-01-08
I didn't take offence and I hope I didn't offend you either :) My apologies if came out that way :)

---

### Post by rvchari on 2011-01-08
i had to remove wine and re-install for issues (i felt i might ve made some initial mistake) i followed by adding up a task...
.local folder in home where some apps in wine used to show up...
all said and done, the wine bar from start menu list keeps showing up !!!

---

