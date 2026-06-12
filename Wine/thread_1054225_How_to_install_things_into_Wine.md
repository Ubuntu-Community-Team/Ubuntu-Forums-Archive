---
title: "How to install things into Wine"
date: 2009-01-29
forum: Wine
---

### Post by merkourio on 2009-01-29
Hi to all!
I am new in using linux, but not in computing (GCE A lvl:popcorn:), an d i don't understand how to intall things into wine....
Every answer would help...
Thanks alot, 
Merkourio

---

### Post by icheyne on 2009-01-29
[https://help.ubuntu.com/community/Wine#Installing%20Windows%20Applications%20Using%20Wine](https://help.ubuntu.com/community/Wine#Installing%20Windows%20Applications%20Using%20Wine)

---

### Post by cogadh on 2009-01-29
Current versions of Wine aren't that complicated. Once Wine is installed, it associates itself with the .exe file format, so all you have to do is double-click on it, just like you would in Windows. You only really need to run it from the terminal if the installation or application is giving you problems. Wine will output its error messages to the terminal so that can be used for troubleshooting purposes.

---

### Post by merkourio on 2009-05-03
Tnx to everybody!

---

### Post by Pushpalanka on 2011-04-22
I installed Wine from Software Center. But when I try to install foxit reader.exe by double clicking it give the following error message.
"The file '/home/pushpalanka/Downloads/FoxitReader431_enu/Foxit Reader.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."

I want to run Foxit reader in ubuntu for highlighting. The existing Xournal, okular etc. are not giving that function in a satisfactory level.

Some help please:(:(

---

### Post by cogadh on 2011-04-22
You really should search the forums before posting, especially before posting in a thread that is two years old and quite dead. This question has been asked and answered more times than I can count on these forums.

This is a very common error due to changes in Ubuntu's security policy; no executables from outside sources (downloads, removable media, etc.) are executable by default. You need to right-click on the executable you are trying to run, go to the Permissions tab and check the box for allowing it to run as an executable, then Wine should have no problem with it.

---

