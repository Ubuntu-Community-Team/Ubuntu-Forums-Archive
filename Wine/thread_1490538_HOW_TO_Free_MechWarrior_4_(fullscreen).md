---
title: "HOW TO: Free MechWarrior 4 (fullscreen)"
date: 2010-05-22
forum: Wine
---

### Post by lha on 2010-05-22
How to install and play free MechWarrior 4 in fullscreen mode:

1 ) Install Wine (preferably the latest version, see [https://launchpad.net/~ubuntu-wine/+archive/ppa]("https://launchpad.net/~ubuntu-wine/+archive/ppa")), and the packages winetricks and xdotool.

2 ) Download MechWarrior 4 from [http://www.mektek.net/index.php?pid=13]("http://www.mektek.net/index.php?pid=13"). Grab the MTX installer/client (SetupMTX1.0.3.5.exe), the game itself (mechwarrior4mercenaries.all.to.51.03.01.0017.mtx) and patches (mechwarrior4mercenaries.51.03.01.0017.to.51.03.01.0018.mtx, mechwarrior4mercenaries.51.03.01.0018.to.51.03.01.0020.mtx, etc.).

3 ) Install dotnet20 using winetricks.

4 ) Install MTX client program with Wine.

5 ) Start MTX client (mtx.exe). When mtx.exe starts, it will display two error messages: First one has title "MTX". DO NOT press any of the buttons, just move the dialog out of the way. The second error message has the title "MekTek X (MTX) - Version 1.0.3.5". Press Continue-button to get rid of the dialog. At this point, we have a (partially working) MTX client.

6 ) Install MechWarrior. In the MTX client, open "File" menu and choose "Open File (*.mtx)". (In fact, you won't be able to see the menu bar due to a graphical glitch. However, clicking where the File menu should be works and opens the drop down list.) Pick the file mechwarrior4mercenaries.all.to.51.03.01.0017.mtx in order to install MW4. It will take some time, so be patient...

7 ) Apply the patches using the same method as in step 6). (Remember to apply the patches in correct order, that is, files smaller version numbers first.)

8 ) Edit the file options.ini in the directory where MechWarrior is installed. Change the line "ShadowMode=2" to "ShadowMode=1".

9 ) Download the [launcher script]("http://ubuntuforums.org/attachment.php?attachmentid=157881&stc=1&d=1274545718").

10 ) If you installed MW4 into a non-default directory, you have to edit the script. Open it using a text editor and change the variables WINEPREFIX and INSTALLPATH.

11 ) If you have a CRT monitor, you will probably want to change the variable KEEPRES to have the value "FALSE". This will make the whole game, including menus, mech lab, etc., to be fullscreen. Those with monitors without native support for 800x600 will face the menus in a smallish 800x600 window. However, the actual game engine supports higher resolutions, so within-mech parts of the game are available in fullscreen also for others.

12 ) Start the game by running the script MW4Mercs.sh! From the options menu, choose a resolution that matches your screen's resolution to get the game in fullscreen. (Remember that the menus will always be in a small 800x600 window.)

In fact, this how to provides a fake full screen method for running the Free MechWarrior 4 using Wine. The game works only in windowed mode (see the entry [http://appdb.winehq.org/objectManager.php?sClass=version&iId=5686]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=5686") in AppDB). Fortunately, it is possible to use some tricks to make the game look like it is in fullscreen mode.

Limitations:
-Some parts of the game (menus) are not fullscreen on all computers.
-It takes a while before the game starts. (5-30 s)
-Changing options while in the middle of a mission renders the game unplayable
-Probably something else

All in all, the game is playable in fullscreen! (Instant action and campaign modes work, I haven't tested multiplayer.)

Enjoy. (Comments and questions are, naturally, welcome.)

---

### Post by drink on 2013-02-23
Doesn't work here. What version of wine were you using at the time? Wine has regressions all the time, so "latest version" is not informative.

---

### Post by howefield on 2013-02-23
Old thread closed.

---

