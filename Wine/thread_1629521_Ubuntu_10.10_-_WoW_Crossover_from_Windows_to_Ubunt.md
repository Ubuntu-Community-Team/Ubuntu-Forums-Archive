---
title: "Ubuntu 10.10 - WoW Crossover from Windows to Ubuntu"
date: 2010-11-23
forum: Wine
---

### Post by pockets08 on 2010-11-23
Hi Guys! I always seem to get answers here - so one question real fast.

I recently came back into Linux, but dont wanna send the horrid downtime re downloading WoW. I pulled the WoW folder from the Hardrive, and placed it in the Home/user folder. 
When i double click Launcher.exe - i get a string of errors.

If i pull the launcher form the WoW folder and place it in the Home/user folder - blizzard tells me i need to put it back :P

So - how do i run the command int he terminal?

i have tried 
```
wine /home/user/World of warcraft/launcher.exe
```

but it says cant find directory /home/user/world - so im assuming the spaces are needed to be palced with a symbol? idk - any help here folks?

---

### Post by nixIT on 2010-11-23
you could put the path in quotes, that should work.

---

### Post by cwwilson721 on 2010-11-25
In my setup, I use a "wine" bottle" (in my case, "wine-wow", so change the following command to make yours work (i.e., folder names...Watch the quotes!!)

```
env WINEPREFIX="/home/<USER>/.wine-wow" wine "C:\Program Files\World of Warcraft\Launcher.exe" -opengl
```

This allows me to use other wine programs installed into the same 'bottle', such as Vent. (I don't use it anymore, I now use a Linux client Mangler)

If I need to run wineconfig, I use the following:
```
env WINEPREFIX="/home/<USER>/.wine-wow" winecfg
```
The above configs (and needed after a wine update) the WoW bottle.

Give it a shot.

---

