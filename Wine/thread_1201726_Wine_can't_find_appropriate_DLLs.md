---
title: "Wine can't find appropriate DLLs"
date: 2009-07-01
forum: Wine
---

### Post by ChaosCon on 2009-07-01
Hey all - 

The experimental lab down the hall just gave us some new modeling software to try out - unfortunately they're all Windows and we're all Ubuntu. One of the guys down there said he got this new software working with Wine just fine, but I'm having some real difficulties.  It's not actually anything that just gets installed, but "a group of files we just drag around everywhere." Whenever I try to run the .exe from the GUI, Ubuntu thinks for a second, then just gives up and gives no error or anything. But if I use ```
wine SanGabrielX.exe
``` from the terminal, it throws up various ```
err:module:import_dll Library MSVCP60D.dll (which is needed by L"C:\\Program Files\\Bin\\SanGabrielX.exe") not found

``` errors (for several different DLLs). I was wondering (if you'll pardon my n00biness ):P )- is the problem because nothing ever got installed, so something isn't looking in the appropriate spot? Or is there something else I have to do?

Many thanks!

---

### Post by cogadh on 2009-07-01
Looks like you need to get Visual C++ runtime installed. Get [winetricks]("http://wiki.winehq.org/winetricks") and use that to install it.

---

