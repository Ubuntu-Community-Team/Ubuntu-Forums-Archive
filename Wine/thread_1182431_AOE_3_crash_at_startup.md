---
title: "AOE 3 crash at startup"
date: 2009-06-08
forum: Wine
---

### Post by nategerr on 2009-06-08
I'm having a tough time getting Age of empires3 up and running on my ubuntu. The installation was a mess. fixed a 005d application error, put a bunch of dll's in the /system32 folder , got the right cd crack and downloaded the l3codecx.ax.  Now the game loads to intro but crashes right before the menu screen. I've checked all the forums but the only advice I can find for a crash this late in the load up relates to newprofile.xml.  Any ideas?

---

### Post by ChaiTan on 2009-06-09
I had the same problem, a fix is mentioned on the appdb page.
```
perl -pi.bak -e 's/(.)".4.2."/\0"\0000\0"/' ~/My\ Games/Age\ of\ Empires\ 3/Users/NewProfile.xml
```
Execute the above every time before starting the game or create a script for it.
```
#!/bin/sh
perl -pi.bak -e 's/(.)".4.2."/\0"\0000\0"/' ~/My\ Games/Age\ of\ Empires\ 3/Users/NewProfile.xml
cd ~/.wine/drive_c/Program\ Files/Microsoft\ Games/Age\ of\ Empires\ III/
exec wine age3.exe
```

---

