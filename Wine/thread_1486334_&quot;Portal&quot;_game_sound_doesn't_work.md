---
title: "&quot;Portal&quot; game sound doesn't work"
date: 2010-05-17
forum: Wine
---

### Post by anm112 on 2010-05-17
I recently downloaded Steam and installed the game Portal, but the sound does not work in the game. Sound does sometimes work at startup and at the game menu, but never in the game itself. Can anyone think of a solution to this problem.

Specs: 
Ubuntu 10.04
Wine 1.1.42
AMD Athlon X2
Nvidia graphics card

---

### Post by lightstream on 2010-05-18
What settings do you have under the audio tab in the Wine config tool? (it's the Configure Wine item on the Wine Applications menu, or enter **winecfg** on the command line)

I've found ALSA works best for me. The other one worth trying is OSS, or sometimes I believe people have had results using Esound.

---

### Post by anm112 on 2010-05-18
I tried all of the drivers in the "audio" tab, but none of them worked.

When I start the game for the first time after restarting the computer, audio works in the startup screens and the main menu.  Once I click "start new game" it cuts off, and I get no sound ever again on startup of the game unless I restart my computer.

---

### Post by asdfoo on 2010-05-19
1.1.42 is old.  use 1.1.44 or latest git. there have been sound improvments.

---

### Post by anm112 on 2010-05-19
I tried upgrading to the newest release, but it did not work.

---

### Post by Emmental on 2010-05-23
See here (your Wine thread) for the fix that worked for me:

[http://forum.winehq.org/viewtopic.php?p=43830#43830](http://forum.winehq.org/viewtopic.php?p=43830#43830)

---

### Post by anm112 on 2010-05-31
Thanks for the help guys.  The solution was posted on the wine forum.  I'll quote what the guy said for anyone else who may be having this problem.


> I assume you're running Portal through Steam? Then open the game's properties (right click > properties), click "set launch options" and paste -snd_openal in the box. The game should now try using OpenAL instead of its standard audio system.


---

