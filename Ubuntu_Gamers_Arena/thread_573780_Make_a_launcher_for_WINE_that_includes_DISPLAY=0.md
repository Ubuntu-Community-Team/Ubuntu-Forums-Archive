---
title: "Make a launcher for WINE that includes DISPLAY=:0"
date: 2007-10-12
forum: Ubuntu Gamers Arena
---

### Post by toyota_f1 on 2007-10-12
I am running a RADEON 9600 PRO with Ubuntu Gutsy (beta).  After finally getting everything to work with the built in compiz/visual effects I realize that if XGL is on I can't get DRI and my 3d effects suffer...

The quickest way around this I've found was to use

```
DISPLAY=:0 wine WoW.exe
```

I'm completely new to linux in general and figured I could create a launcher and just use that as a command... it works fine if I leave out DISPLAY=:0, but then I have 3d issues because DRI won't work... as soon as I put the DISPLAY=:0 back I get...

Details: Failed to execute child process "DISPLAY=:0" (No such file or directory)

Any way around this so I don't have to do this through terminal every single time?

Thanks!

Isaac.

---

### Post by Jussi Kukkonen on 2007-10-12
For this instance you can use:
```
env DISPLAY=:0 wine WoW.exe
```
For more complex situations, save the command(s) in a script file and run that file from the launcher

---

