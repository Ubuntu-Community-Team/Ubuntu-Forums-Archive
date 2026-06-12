---
title: "wine 1.1.10 is installing the menues in the &quot;other&quot; category"
date: 2008-12-11
forum: Wine
---

### Post by Meow27 on 2008-12-11
well, ill admit i probably caused this problem when i compiled Wine before installing it from a normal package

so heres my problem
in a normal situation, i install a program under wine and it goes onder my WINE>PROGRAMS/[etc...]

here its installing programs thru OTHER>[etc....]

i removed the compiled version with make uninstall and installed it from a package. ([http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html))

i have tried installing programs after that but the problem persists. is there anyway to solve this problem and get wine to place the menu shortcuts where they belong?

i just reinstalled ubuntu and dont want to go through this again (i had 8.10 installed right after it came out, i didnt have this problem before)

thanks in advance (im running Ubuntu 8.10)

---

### Post by ToasterThief on 2008-12-11
sudo rm -rf .wine

---

### Post by Meow27 on 2008-12-11
> **ToasterThief said:**
> *****************

and why would deleting my wine folder work?

im sorry but im leaving that as the last option because it usually means i should do that command everywhere else after that to get wine working (cause i cant get it to work after i do that)

---

### Post by hikaricore on 2008-12-11
Come on people... the OP said he had other software installed just fine under WINE.
Why in the bloody hell would you tell him to delete his whole WINE folder?

If you can't be bothered to post a sensible response, then don't bother posting.

---

### Post by lady_jade on 2008-12-12
> **Meow27 said:**
> and why would deleting my wine folder work?

im sorry but im leaving that as the last option because it usually means i should do that command everywhere else after that to get wine working (cause i cant get it to work after i do that)

Well I must admit that I tried that code above and suffered the consequences.(that was before the other replies where made saying it would have deleted the wine stuff.)

 Thanks a lot. I guess I can't always trust what is posted here - I am not blaming you for my ignorance though. But please be careful as there are a lot of new ubuntu users on this site. I had to sit down install everything over again - oh the headache that cost me.

---

### Post by chris062689 on 2008-12-12
I also have this problem, any Steam application I install it goes into my "Other" folder, I remember being able to relog and it would update the menu's in earlier releases, but this doesn't seem to be the case.

---

### Post by Meow27 on 2008-12-13
> **lady_jade said:**
> Well I must admit that I tried that code above and suffered the consequences.(that was before the other replies where made saying it would have deleted the wine stuff.)

 Thanks a lot. I guess I can't always trust what is posted here - I am not blaming you for my ignorance though. But please be careful as there are a lot of new ubuntu users on this site. I had to sit down install everything over again - oh the headache that cost me.

the announcements and stickies are there for a reason! :P they explicitly say not to trust things that include "rm rf" or something like that :/

well in other news... due to frustration with intrepid. i have officially downgraded to hardy so i dont think ill be seeing these issues anytime soon (or so i think!)

EDIT----------------------------
apparently this is an issue for this version of wine.....not ubuntu

---

