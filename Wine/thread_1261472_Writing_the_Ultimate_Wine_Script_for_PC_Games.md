---
title: "Writing the Ultimate Wine Script for PC Games"
date: 2009-09-08
forum: Wine
---

### Post by Dark Aspect on 2009-09-08
Hello all,

I would like some help in writing the ultimate wine script. What I would like to do is make a script that disables Compiz, uses wine debug and increases CPU priority. Now, before or on low spec games I usually just use the following

```
cd "/home/administrator/.wine/drive_c/Program Files/Rockstar Games/GTA San Andreas"
WINEDEBUG=-all env WINEPREFIX="/home/administrator/.wine" wine "C:\Program Files\Rockstar Games\GTA San Andreas\gta_sa.exe"
```

Now on more stress intensive games I use this"

```
#!/bin/bash
cd "/home/administrator/.wine/drive_c/Program Files/Activision/Wolfenstein/SP"
WINEDEBUG=-all env WINEPREFIX="/home/administrator/.wine" wine "C:\Program Files\Activision\Wolfenstein\SP\Wolf2.exe" &&
renice -n -20 -p `pidof Wolf2.exe` && 
exit
```

Now, how can I modify the last script to integrate disabling and enabling compiz? Also am I using renice -n -20 correctly? Should the game (.exe) be the target of renice or wine itself?

Is there anything else I can do to increase performance in wine?

---

