---
title: "An inability to install Wine, and therefore anything else."
date: 2010-10-31
forum: Wine
---

### Post by CrispyFriedUke on 2010-10-31
I am brand spanking new to Linux. I've had Ubuntu on my laptop for maybe a week and a half, because when it broke we were unable to put anything else on it, so my friend (You know which friend, the one that's 'that computer guy') downloaded Ubuntu for me.

Today I finally got around to trying to install my tablet driver, iTunes, photoshop, and the like, still in a windows state of mind. I searched around and learned I needed to install Wine to do so.

One problem:
I go to System->Administration->Software Sources->Third-Party Source->Add, and I type in exactly what is on the WineHQ site, and It won't let me click 'Add Source' after I put it in. I tried copy paste, I tried typing it out, but to no avail. Is there anyway to fix this problem and add Wine, or is there any other software I can attempt to add so I can download things like iTunes and my tablet driver?

---

### Post by CrispyFriedUke on 2010-10-31
Might I add that if I need to I'm willing to take screenshots of what I'm doing and what it looks like!:biggrin:

---

### Post by ebasa on 2010-10-31
Wine, as much as I would never use it should be in the repositories,open Synaptic and search for it, should be in Cross Platform (UNIVERSE).

---

### Post by uRock on 2010-10-31
I recommend looking here before fighting to install Photoshop or iTunes in Wine. 

Wine ratings for iTunes [http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347)

Wine ratings for photoshop [http://appdb.winehq.org/objectManager.php?sClass=application&iId=17](http://appdb.winehq.org/objectManager.php?sClass=application&iId=17)

And yes, Wine is easily install via Ubuntu Software Center.

---

### Post by CrispyFriedUke on 2010-10-31
Oh! Well that was intensely simple. Thank you! Hopefully from here on it will go wihout a hitch, though may I ask why you would never use it?

---

### Post by uRock on 2010-10-31
> **CrispyFriedUke said:**
> Oh! Well that was intensely simple. Thank you! Hopefully from here on it will go wihout a hitch, though may I ask why you would never use it?
Many people feel that it is best to run Windows programs in Windows.

Moved to the Wine sub-forum.

---

### Post by ebasa on 2010-10-31
> **CrispyFriedUke said:**
> Oh! Well that was intensely simple. Thank you! Hopefully from here on it will go wihout a hitch, though may I ask why you would never use it?

I don't want anything windows related on my computer. If I was into gaming maybe, but I am not. There is nothing I do that Linux cannot do for me.

---

### Post by cogadh on 2010-11-01
> **CrispyFriedUke said:**
> Today I finally got around to trying to install my **tablet driver**...
Well, that's not going to work, even if you do get Wine installed correctly. Wine is only for running (some) Windows *applications*, not operating system components like drivers.

Also, you may find some "Linux purists" have some strong opinions about using Wine. Don't take it too personally. Linux is all about the freedom of choice, including the freedom to choose to run Windows software on your Linux machine through Wine. Generally speaking, it is almost always better to use a Linux native alternative to a Windows app (if available), but there is nothing wrong with choosing to continue to use the Windows software you are comfortable with (assuming it works in Wine).

---

