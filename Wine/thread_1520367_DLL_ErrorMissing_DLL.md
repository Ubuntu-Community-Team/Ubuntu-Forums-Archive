---
title: "DLL Error/Missing DLL"
date: 2010-06-29
forum: Wine
---

### Post by Seanlol on 2010-06-29
SOLVED

Something like this has probably been asked before, but the search feature isn't giving me anything useful.

I'm trying to install a program called RavenDice using Wine. When I do this, I get an error saying I'm missing a DLL. Here's my error

[[IMG]http://img412.imageshack.us/img412/2849/wineerror.png[/IMG]]("http://img412.imageshack.us/i/wineerror.png/")

Is there anywhere I can download this DLL? If so, where do I put the DLL? in the Windows folder of the virtual C: Drive?

---

### Post by cogadh on 2010-06-29
That DLL is part of Visual Basic Runtime, specifically VB6. You can install that using [winetricks]("http://wiki.winehq.org/winetricks").

---

### Post by Seanlol on 2010-06-29
> **cogadh said:**
> That DLL is part of Visual Basic Runtime, specifically VB6. You can install that using [winetricks]("http://wiki.winehq.org/winetricks").

I got winetricks and installed VB6 runtime. The program attempts to open now, but I'm getting another error message now. 

Is there something else I can install via Winetricks to get the "Mscomctl.ocx" file?

[[IMG]http://img404.imageshack.us/img404/7991/newerror.png[/IMG]]("http://img404.imageshack.us/i/newerror.png/")

EDIT: Solved. Downloaded the file from [http://www.ascentive.com/support/new/images/lib/MSCOMCTL.OCX](http://www.ascentive.com/support/new/images/lib/MSCOMCTL.OCX) and put the file in the system32 folder of the C: drive. 


Thanks for the help

---

### Post by cogadh on 2010-06-29
For future reference, winetricks can install that for you. If you check the page I linked to in my original post, it lists all the things winetricks can do. Items 8 and 9 on the list of packages it can install include the ActiveX control modules you needed.

---

