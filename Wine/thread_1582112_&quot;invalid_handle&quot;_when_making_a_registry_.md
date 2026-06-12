---
title: "&quot;invalid handle&quot; when making a registry key?"
date: 2010-09-26
forum: Wine
---

### Post by Simplebear on 2010-09-26
Hello I am trying to install perfect world on my Ubuntu. 
 
Ubuntu 10.04 lynix 
Wine1.2
 
Ok so i opened up the registry and went to current user then down to software and down to wine. 
 
the instructions were to right click on wine and create a new key called Direct3D but when i click on key i get "Invalid Handle"
 
Does anyone know how to fix this?

---

### Post by Simplebear on 2010-09-26
Anyone?:(

---

### Post by StrayCatalyst on 2010-10-03
I'm having a similar problem running City of Heroes under Lucid.  I have wine 1.1.42, and have (after much forum searching and work) managed to get the installer and updater for the game to run, but when the updater completes its work and tries to load the game, it goes to the first loadscreen and never proceeds further - I've let it sit on that loadscreen for as long as eight hours, so it's not just a slow load.

When I try "Browse Drive C:" in the wine folder, it gives the following error message:
p, li { white-space: pre-wrap; } Unable to run the command specified. The file or folder file:///home/moose/Documents/.wine/dosdevices/c: does not exist.


When I try running the game from the terminal, it gives me this error, similar to SimpleBear's:
moose@David-desktop:~$ wine /home/moose/.wine/dosdevices/c:/Program\ Files/City\ of\ Heroes
wine: Invalid handle


I'm not sure if that's related, I'm an ubuntu newbie and learning things the hard way.  Any idea what I should try next?  Wine appeared to work for the installer, and the updater runs similarly to how it did under winXP.


Stray

---

### Post by Simplebear on 2010-10-03
the fix for me was to reinstall wine

---

### Post by StrayCatalyst on 2010-10-03
I already did, which didn't change the symptoms any...  I also changed permissions on all of the game's .exe files, set wine to run emulation for audio, and to run as a virtual desktop, per the advice of a variety of other threads I've followed where users had similar problems to mine.  The problem is, I've been unable to find any threads where the problem described is quite the same as the one I've got.  I'd rather not give up and go back to Windows, as I have enough frustrations and problems with that OS already.

Stray

---

### Post by Simplebear on 2010-10-03
the most current wine is 1.3... have you tried updating it?

---

