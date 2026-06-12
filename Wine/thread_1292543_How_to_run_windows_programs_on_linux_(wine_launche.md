---
title: "How to run windows programs on linux (wine launcher)"
date: 2009-10-16
forum: Wine
---

### Post by caspertk on 2009-10-16
========================================================
================Using Widnows Programs on Linux==================
========================================================
=====================Written by Kaspir========================

----------------------------------------------------------------------------------------------------
               I wrote this for a friend and figured I would share it with everyone. 
----------------------------------------------------------------------------------------------------
To begin, download your file. It will most likely end in .exe.

Example:     install.exe

Right click on this and select "open with 'Wine Windows Program Loader'"

After installing, go to the top left corner of the desktop and right click on "Applications", then select "Edit Menus"

A window will pop up with two different sections. On the left, "Menus", and on the right, "Items".

Near the bottom of the menus portion, select wine. The left hand side of the window will refresh, and display the items in the wine menu.

All the way to the right click on "New Item". Another window will appear titled, "Create Launcher".

Type should always be "Application", Name is obviously the name of the game/program.

Command is what we are interested in. Leave that window open and go back to the applications menu at the top left. Left click this time and select "Wine -> Browse C:/ Drive" 

In here, there are a number of folders. "Program Files" is what we need to select, so double click.

When you ran the instal.exe, it installed the program into your "Virtual C:/ Drive" which is what you are browsing right now. You don't actually have a C:/ Drive but wine is emulating one for the specific purpose of running windows programs. When I installed the Pirates of the Caribbean, for instance, it created a folder called Disney. So any other Disney games, you download will go in here.

If you were to download a game from ubisoft, the game would most likely go in a ubisoft folder created upon install. 

Now navigate through the folder untill you find a file simular to "Launcher.exe" or "Run.exe". Stay away from any files that resemble "Uinstall.exe". This is an unistall command.

Now right click on "Launcher.exe" (we'll use this name for the sake of this tutorial) and right click, then select properties.

Next to location should be a very long string of text. 

/home/dayrl/.wine/dosdevices/ is unimportant. So copy from the end of that over.

c:/Program Files/Disney/Disney Online/PiratesOnline

The above is the string of text you would need to run Pirates of the Caribbean. 

Now go back to the "Create Launcher" window and (in the command section) type "wine", press space once, and paste the portion you copied earlier.

Right after the end of the text you pasted, type "/launcher.exe". Replace "launcher" with the actual .exe used to launch the game/program.

Type what you want to be displayed when you hover over the shortcut in "Comment".

So for pirates of the caribbean the "Create Launcher" window should now look like Create_Laucher.png. Found in the same folder as this tutorial.

Now simply click on close, navigate to the shortcut (Applications -> Wine -> Pirates of the Carribean) and your game/program should start up!

---

### Post by bapoumba on 2009-11-05
Moved to Wine.

---

