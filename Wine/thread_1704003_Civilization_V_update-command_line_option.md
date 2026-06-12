---
title: "Civilization V update-command line option"
date: 2011-03-10
forum: Wine
---

### Post by sigma_z_1980 on 2011-03-10
hi, I'm trying to update Civ5 in Ubuntu. I'm trying to run 

    wine 'C:\Program Files (x86)\Steam\bin\Steamservice.exe /Install'

The last option is a problem 'cause I'm getting the message that the file couldn't be found. Any suggestion on how I can run it?

 cheers

---

### Post by cogadh on 2011-03-10
Try running it like this:
```
wine ~/.wine/drive_c/Program\ Files\ (x86)/Steam/bin/Steamservice.exe /Install
```
Or, change directories to the executable's directory first, then skip the whole path part in the command:
```
cd .wine/drive_c/Program\ Files\ (x86)/Steam/bin
wine Steamservice.exe /Install
```
However, are you certain that it is actually installed in "Program Files (x86)" and not just plain old "Program Files"? I didn't think Wine used that particular quirk of 64 bit Vista and Win 7 yet.

---

