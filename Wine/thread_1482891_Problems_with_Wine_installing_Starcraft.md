---
title: "Problems with Wine installing Starcraft"
date: 2010-05-14
forum: Wine
---

### Post by Phobiaz on 2010-05-14
I recently switched to Ubuntu 10.04 from Windows XP. 
Downloaded Wine from "Ubuntu Software Center" hoping to install Starcraft.
Now, when I right click "SETUP.EXE" or "INSTALL.EXE" within the Starcraft disc Image and choose Open With "Wine Windows Program Loader" (Under Application it says: cautious-launcher) It gives me this error: 

"The file 'home/myname/.cache/.fr-uLd4w/INSTALL.EXE;1' is not marked as executable. If this was downloaded or copied from an untrusted source, it may be dangerous to run. For more details, read about the executable bit."

Any help or advice on this error will be appreciated. Thanks.

---

### Post by Elvish Legion on 2010-05-14
> **Phobiaz said:**
> I recently switched to Ubuntu 10.04 from Windows XP. 
Downloaded Wine from "Ubuntu Software Center" hoping to install Starcraft.
Now, when I right click "SETUP.EXE" or "INSTALL.EXE" within the Starcraft disc Image and choose Open With "Wine Windows Program Loader" (Under Application it says: cautious-launcher) It gives me this error: 

"The file 'home/myname/.cache/.fr-uLd4w/INSTALL.EXE;1' is not marked as executable. If this was downloaded or copied from an untrusted source, it may be dangerous to run. For more details, read about the executable bit."

Any help or advice on this error will be appreciated. Thanks.

try

wine /path/to/INSTALL.EXE

Also if that doesn't work you could try downloading it from your battle.net account

---

### Post by Phobiaz on 2010-05-14
Thank you for the reply Elvish Legion. I tried running it through terminal with no success.
Also, I believe this error might simply be with all Blizzard Games (I tried WC3 and Starcraft). 
Wine works just fine on other programs I've tested such as Guitar Pro 5.

If anyone can help, please reply. 
Thanks again

---

### Post by rJ~ on 2010-05-14
Googling for "Executable Bit" gave this result:
[http://ubuntuforums.org/showpost.php?p=9045197&postcount=8](http://ubuntuforums.org/showpost.php?p=9045197&postcount=8)

If that doesn't work, I'd suggest the same as Elvish Legion. I've downloaded and installed Diablo 2 with the battle.net installer.

---

### Post by Elvish Legion on 2010-05-14
> **Phobiaz said:**
> Thank you for the reply Elvish Legion. I tried running it through terminal with no success.
Also, I believe this error might simply be with all Blizzard Games (I tried WC3 and Starcraft). 
Wine works just fine on other programs I've tested such as Guitar Pro 5.

If anyone can help, please reply. 
Thanks again

Can you post the exact error message? I've never ran into a problem with blizzard games (except when the downloader was brand new)

---

### Post by Alonso J. on 2010-06-02
Phobiaz:

I had exactly the same error (the same Ubuntu version (10.04) and the same game (Starcraft))
Now I finally solved it (maybe not fixed, but solved)

Try this:

Right-click on the setup.exe file, and choose "open with another aplication" ("abrir con otra aplicación" in Spanish, don't really know how it is in English)

There, use your own command --> "wine" (without the "" )

That worked perfectly for me.
Now, every time you open the file, do not use the "Open With Wine Windows Program Loader" option, instead use the "open with wine" option that now should appear there

Hope it works for you as well

---

### Post by McRat on 2010-06-03
Not sure if this is right:

I loaded it using Crossover.

Create Bottle Win98, named it Starcraft.

RUN Setup.exe from the same Manage Bottle screen.

Runs excellent.  I had a little heartburn doing the 1.6.1 (latest) patch, but it amounted to downloading the patch itself (NOT FROM BATTLENET) and installing with the Starcraft bottle I created.

---

### Post by redconfusion on 2010-07-11
Didn't have any problems installing this via client download from battle.net after you registered your game there.

Single player works fine but battle.net doesn't work for multiplayer, had to use chaoslauncher (3rd party launching tool) to force windowed mode to get multiplayer to work.

*edit: game crashes when you try to change game channel, everything else seems to work.

---

