---
title: "Help with wow running on Wine."
date: 2009-02-03
forum: Wine
---

### Post by M!SF!TS on 2009-02-03
Well, i completely switched to linux, EXCEPT for 1 program PureEdge, (I have to use it sayd the army) Anyways i want to play World Of Warcraft, and i read this... ( [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) ) and it got me stuck

i get to this part
Do this in Terminal : 
 #cd /<path-to-directory>/
 #wine Installer.exe

and yeah... i do it and i get a message that says this:

____________________________________________________________
|___INSTALLER_______________________________________________|
|  Sorry, The installer was unable to start up.             |
|___________________________________________________________|
|No installer data could be found. If this problem persists,|
|please contact Blizzard                                    | 
|Technical Support.                                         |
|                                                           |
|                                                           |
|                                                           |
|                                                           |
|                                                           |
|                                                           |
|                                                           |
|                                                           |
|___________________________________________________________|
|                                           ______________  |
|                                           |_____OK______| |
|___________________________________________________________|

(^^This is a window box^^)

so what do i do now ?
how do i get freaking World Of Warcraft to play on wine ?

anyone know 

i am going to bed i have to wake up and goto work tomorrow, (as you can see i spent my entire time off today after work trying to figure this animal out but got no where) so sorry if i dont answer back but i am dying to get this thing to work!!! anyways i hope you liked my art work and any help will be appreciated and i will get back to this post A.S.A.P. when i get off work tomorrow!!!

Thanks
-Misfits

---

### Post by Vadi on 2009-02-03
Calm down man :)

Try re-downloading the installer, it could have been corrupted. You can also just double-click on the .exe file to start it.

---

### Post by gjoellee on 2009-02-03
try double click on the .exe

---

### Post by |{urse on 2009-02-03
You should also try never attempting ascii art again, ever, please.

:lolflag:

---

### Post by bapoumba on 2009-02-03
Moved to Wine and edited the title.

---

### Post by xx.canes.rites on 2009-02-03
> **M!SF!TS said:**
> Well, i completely switched to linux, EXCEPT for 1 program PureEdge, (I have to use it sayd the army) Anyways i want to play World Of Warcraft, and i read this... ( [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) ) and it got me stuck

i get to this part
Do this in Terminal : 
 #cd /<path-to-directory>/
 #wine Installer.exe

and yeah... i do it and i get a message that says this:

____________________________________________________________
|___INSTALLER_______________________________________________|
|  Sorry, The installer was unable to start up.             |
|___________________________________________________________|
|No installer data could be found. If this problem persists,|
|please contact Blizzard                                    | 
|Technical Support.                                         |
|                                                           |
|                                                           |
|                                                           |
|                                                           |
|                                                           |
|                                                           |
|                                                           |
|                                                           |
|___________________________________________________________|
|                                           ______________  |
|                                           |_____OK______| |
|___________________________________________________________|

(^^This is a window box^^)

so what do i do now ?
how do i get freaking World Of Warcraft to play on wine ?

anyone know 

i am going to bed i have to wake up and goto work tomorrow, (as you can see i spent my entire time off today after work trying to figure this animal out but got no where) so sorry if i dont answer back but i am dying to get this thing to work!!! anyways i hope you liked my art work and any help will be appreciated and i will get back to this post A.S.A.P. when i get off work tomorrow!!!

Thanks
-Misfits


Go to [http://www.worldofwarcraft.com](http://www.worldofwarcraft.com) go to manage accounts, enter your acc info and password. Go to download game client, get the pc universal installer and use that instead of trying to install via DVD or CDs, WINE likes the installer from wow.com alot better.
Also when you download the pc installer from wow.com just install the Lich King and all others will be installed, too, instead of installing all three separately.

---

### Post by M!SF!TS on 2009-02-04
Okay i got back from work and i am installing it and downloading it, but i have to goto bed agian and goto work tomorrow i will post again on the result after the download and install, and this is what i did

1. downloaded wine... blah blah, and ran this in terminal once it was installed
  #winecfg
2. setup the winecfg
3. logged on to the worldofwarcraft.com site downloaded the universal pc installer
4. ran it, and saved the download / installer into home/<myname>/Documents/Games/WorldOfWarcraft

and thats as far as i got so far, will post again tomorrow !

(i dont even care about the game LOL i just NEED to figure out how to do this ifs fun!!!)

-Misfits

---

### Post by Mister Fowler on 2009-10-26
I am also trying to use the installer but when I scroll to the bottom of the EULA, the Accept button doesn't enable. Any idea why?

---

### Post by beastrace91 on 2009-10-27
> **Mister Fowler said:**
> I am also trying to use the installer but when I scroll to the bottom of the EULA, the Accept button doesn't enable. Any idea why?

What Wine version are you using? If you are using the default "stable" version from the Ubuntu repos are you are going to want to upgrade to the beta packages as they add ALOT of functionality.

If you are not sure about your current Wine version run ```
wine --version
``` in terminal.

~Jeff

---

### Post by Mister Fowler on 2009-10-27
> **beastrace91 said:**
> What Wine version are you using? If you are using the default "stable" version from the Ubuntu repos are you are going to want to upgrade to the beta packages as they add ALOT of functionality.

If you are not sure about your current Wine version run ```
wine --version
``` in terminal.

~Jeff
That did it, thanks. I am installing now. Thank you.

---

