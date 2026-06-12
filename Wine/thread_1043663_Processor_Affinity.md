---
title: "Processor Affinity"
date: 2009-01-18
forum: Wine
---

### Post by The Joe on 2009-01-18
Thief: The Dark Project has a known bug that causes it to lock up on Hyperthreading/Dual Core systems. I have the latter.

Is there any way I can permanently change the processor affinity of the .exe / wine?

---

### Post by The Joe on 2009-01-19
Eeeny weeny tiny winy bump

---

### Post by xzero1 on 2009-01-19
Get and try running wine with "schedtool".

---

### Post by The Joe on 2009-01-19
Tried it - it messes up my resolution a bit then immediately closes.

---

### Post by The Joe on 2009-01-21
Another bump.

---

### Post by happyhamster on 2009-01-21
- To set affinity for core 1 (from a terminal):

taskset -c 0 wine program_name.exe

- or for core two:

taskset -c 1 wine program_name.exe

- If you want to use the taskset command with a menu-launcher: right-click the menu-panel, and choose Edit Menus and keep searching in the left-pane until you have the desired folder selected. Then highlight the correct launcher in the right pane and choose properties. You can then make the desired changes in the "Command" field.
For example, in my case of Tomb Raider Anniversary: in the menu-structure I would have to select the folder Wine-->Programs-->Eidos-->Tomb Raider - Anniversary and highlight the Tomb Raider - Anniversary entry in the right panel. The Command field shows:
 
env WINEPREFIX="/home/username/.wine" wine "C:\Program Files\Tomb Raider - Anniversary\TRA.exe" 

- Which I would change into:

env WINEPREFIX="/home/username/.wine" taskset -c 0 wine "C:\Program Files\Tomb Raider - Anniversary\TRA.exe"

- If you're using a desktop icon to start the game, you can probably right-click it and follow a similar procedure.

Good luck, and keep us informed.

---

### Post by The Joe on 2009-01-23
Thank you - I'll give it a try

---

### Post by The Joe on 2009-01-24
That worked =) Thank you very much

---

### Post by The Joe on 2009-01-24
Ok scratch that - I'm using another program, DarkLoader to load Thief because of some patches and things that allow it to run better. DarkLoader runs fine with taskset but Thief is still locking up, running on both cores.

---

