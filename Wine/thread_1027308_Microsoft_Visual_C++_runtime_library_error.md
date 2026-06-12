---
title: "Microsoft Visual C++ runtime library error"
date: 2009-01-01
forum: Wine
---

### Post by b3n0 on 2009-01-01
Hey guys,
My uncle has been working on a program that he wrote in jade. The program is a stand alone .exe. It installs fine but it gives me this error when its run.
[IMG]http://fc06.deviantart.com/fs39/f/2009/001/d/b/error1_by_B3N0.png[/IMG]
My uncle said that I need to find a C++ runtime environment for wine. Is this right? Can anyone give me a hand with that? Please :) 
I'm running wine version 1.1.10
Thanks again.

---

### Post by OrbJinzo on 2009-01-01
Youll prolly have to install the run time via a script called wine tricks 

[http://wiki.winehq.org/winetricks?highlight=(wine)|(tricks](http://wiki.winehq.org/winetricks?highlight=(wine)|(tricks))

---

### Post by b3n0 on 2009-01-01
> **OrbJinzo said:**
> Youll prolly have to install the run time via a script called wine tricks 

[http://wiki.winehq.org/winetricks?highlight=(wine)|(tricks](http://wiki.winehq.org/winetricks?highlight=(wine)|(tricks))

Thanks mate, I forgot I had wine tricks installed. It should make it allot easier.

---

### Post by b3n0 on 2009-01-02
I'm still getting that same error.
I installed all for the following using winetricks

vcrun6        MS Visual C++ 6 sp4 libraries (mfc42, msvcp60, msvcrt)
vcrun2003     MS Visual C++ 2003 libraries (mfc71,msvcp71,msvcr71)
vcrun2005     MS Visual C++ 2005 libraries (mfc80,msvcp80,msvcr80)
vcrun2005spl  MS Visual C++ 2005 sp1 libraries
vcrun2008     MS Visual C++ 2008 libraries (mfc90,msvcp90,msvcr90)

Would I need to replace any .dll's in the system32 folder? Is there anything else I should install?
Thanks

---

### Post by creek23 on 2009-01-02
You are having problem with "C" runtime -- not C++.

---

### Post by b3n0 on 2009-01-02
Any idea what the c runtime library command for winetricks would be?

---

### Post by Shalmainia on 2010-10-03
Also experiencing the problem with Requiem: Momento Mori (Horror MMORPG). Tried the wine-tricks to no avail. Really would love some assistance.

---

### Post by pedro_orange on 2010-10-05
Shalmainia - please run the application from the command line and check the output. 

Outlook doesn't look good: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=7695](http://appdb.winehq.org/objectManager.php?sClass=application&iId=7695)

---

