---
title: "Wine/Ubuntu lockup with &quot;Treepad&quot;"
date: 2009-01-04
forum: Wine
---

### Post by jbuczek on 2009-01-04
Be gentle, I'm a linux nube although I spent 30 in the computer industry.

I'm trying to convert from Win to Ubuntu.  My most critical program is a freeform textbase called Treepad, specifically the TreepadBZ version.

The vendor says "TreepadBZ works under some combinations of linux/Wine." They have not specifically tested Ubuntu and the latest Ubuntu supported Wine release.

The program starts normally.  I can fill out the registration screen and choose from "Basic/Advanced" and can choose the data file from startup utility windows.  The data file loads correctly and I can choose and examine any record as long as I stay away from the menu bars.

Once the main window opens, if I select anything on the main menu line the drop down opens.  As soon as I click again ... anywhere in the Wine window, the computer freezes.  The mouse will not move and no key stroke combination will do anything.  I cannot find any way to break out of Wine to kill the process.  The only way out I've found is to power off the computer.

Even if I don't touch anything on the menu bars, if I click outside the Wine window, i.e. anywhere in the Ubuntu desktop, as soon as I click again anywhere in the wine window the same lockup happens.

This is 100% and exactly repeatable. The same thing happens if I use hot keys to call the menu options.

Question is: is this something that it is likely could be fixed by config changes in wine?  Maybe by replacing one or more Wine DDL's with original WinXP DDL's.  I have a open, non-upgrade CD of XP purchased directly from MS so I can substitute lib's legally.

The company sells a version of Treepad specifically for Linux/Wine but it's one level down and I'd like to avoid losing features if I can.

I'm running Ubuntu 8.10 on a Jetway mb with a Via 1.2 ghz cpu and 1 GB RAM.  The wine configuration was given 0.5GB RAM.  I've been running Ubuntu on it for weeks with no problems.

TIA

---

### Post by Eviljim on 2009-01-05
Hi there,

Im not a user of Treeview myself, but I thought I could throw a suggestion your way.

Looking at the treeview website, they obviously have windows versions as well as 2 linux ones available.

I would guess that the windows version you are trying to run through wine requires extra dll's that do not come with this version as its windows specific.

The Linux version mentions the Kylix libraries are required for the Linux versions to run

[http://www.treepad.com/linux/libraries/]("http://www.treepad.com/linux/libraries/")

Now maybe getting these libraries and adding them to Wine, may be a solution you might want to investigate.

p.s another thing to check is the permission settings for the folder that contains Treeview, as it may have restricted it to root writing only.


Let me know how you get on..

Cheers

---

