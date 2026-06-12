---
title: "Menu in initial wxSmith program does not show up in 11.10"
date: 2012-02-02
forum: Ubuntu Dev Link Forum
---

### Post by Clopper Almon on 2012-02-02
When a wxSmith application is started in Code::Blocks, a small application is created which has a two-item menu and a blank screen. It runs perfectly in 10.04. In 11.10, the menu does not show up. The Code::Blocks version is 10.05 in both cases, and the C++ code is identical. In good old 10.04 everything is fine, but in 11.10, the same program fails to show its menu.   

I am using the Gnome 3 desktop.(I worked with Unity for a few days, became reasonably proficient, but found it far less convenient than the old desktop.)

Any help or even any indication that others have or do not have this problem would be appreciated.

---

### Post by Clopper Almon on 2012-02-02
I can now add that if I bring the executable file created on Ubuntu 10.04 over to the machine with Ubuntu 11.10, do chmod a+x on the file, and run it on 11.10, the menu shows up fine.

On Ubuntu 11.10, I can add to the wxSmith starter file buttons, labels, and text controls; and they all show up fine. So wxWidgets seems to be installed fine. It is just the main menu of programs compiled and linked on 11.10 that seem to be the problem.

---

### Post by Clopper Almon on 2012-02-02
Kindly souls on the Code::Blocks forums have pointed out that wxGTK2.8.12 fixed a problem that caused the main menu not to appear on some systems, of which Ubuntu 11.10 is apparently one. But the Ubuntu repositories have only wxGTK2.8.11. 

Does anyone know how to get the repositories updated or to use the files directly from the developer?

---

### Post by Clopper Almon on 2012-02-05
I pursued this bug on the launchpad site. The bug was detected and reported within a few days of the release 10.10, the first with Unity. The bug is number 662077. Apparently it is well known what needs to be done to fix the bug -- just add 3 or 4 lines of code somewhere -- but a year has gone by without it actually getting fixed in the system an ordinary Ubuntu user encounters.

What worked for me was to follow a suggestion I found there and remove appmenu-gtk. For greenhorns like me, I may add that I did this in the Gnome3 desktop for Ubuntu 11.10 by clicking Applications in the main menubar, then clicking Ubuntu Software Center, and then entering [FONT="Courier New"]appmenu-gtk [/FONT]in the search field in the upper right corner. That brings up a line with the words "Export GTK menus over DBus" on the left side. Click those words and a wide orange bar comes up with with a button labeled "Remove" on the right. Click that button. 

This bug was not in Ubuntu 10.04 and seems to have been a by-product of Ubuntu work on Unity.

---

