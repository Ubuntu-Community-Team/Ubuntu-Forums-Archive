---
title: "Problem in age of mythology"
date: 2009-03-04
forum: Wine
---

### Post by kmittal on 2009-03-04
I installed this game on windows xp, but I could access it on linux using wine, till the day I upgraded wine. Now I am getting the following error on execution:
"unable to determine the status of installed video card"
Is there any method which does not involve downgrading wine?
If no, how to downgrade wine to some older version without any problem?

---

### Post by cogadh on 2009-03-04
What Wine version did you upgrade to? 

The way you were running the game could be a factor. Wine is not supposed to be used to access an existing Windows installation and can in fact damage it. Because of this, current versions of Wine do have processes in place to prevent you from doing that. You might try using Wine as intended and install the game within Linux through Wine to see if that makes a difference.

---

### Post by kmittal on 2009-03-04
I upgraded wine to 1.1.15 using package manager. I cannot install aom again as I do not have setup files. I want the procedure to either
i. Solve this problem specifically
ii.Restore the system to an earlier date or
iii. Completely remove wine and install a new copy of wine 1.0.1 (it sounds 
    easy but isn't)
Thanks :)

---

### Post by cogadh on 2009-03-04
It's actually very easy to go back to 1.0.1:
1. Uninstall Wine
2. Open up Software Sources (found under System > Adminstration) and remove the WineHQ repository
3. Re-load sources (should happen automatically IIRC)
4. Reinstall Wine from Ubuntu's default repository (version 1.0.1).

---

