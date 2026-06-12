---
title: "is it possible to...."
date: 2009-01-09
forum: Wine
---

### Post by gettensome on 2009-01-09
Just wondering if it is possible to add something to a command line that will automatically switch my Window manager from Compiz to metacity when I run an application in wine?

to be specific,  I want to run World of Warcraft in windowed mode, something that doesn't work very well under Compiz.  So What I'm looking for is possible a command line operator that will force my desktop into metacity while that application is running.  If this is not possible from the CL,  is there any other workaround someone knows of?

---

### Post by kostkon on 2009-01-09
You can install [*fusion-icon*]("http://packages.ubuntu.com/intrepid/fusion-icon"). It will put an icon in your taskbar to allow you to easily switch between Compiz and Metacity.

---

### Post by ajgreeny on 2009-01-09
Or you can make a simple script file which changes the window manager to metacity and then opens your game, and then when you stop playing the game changes back to compiz.  You will then need to make that script file the target of your game's menu shortcut launcher.

---

### Post by binbash on 2009-01-10
+1 for fusion-icon

---

### Post by gettensome on 2009-01-10
-1 for fusion-Icon, +1 for witting a script to do it for you.  Not to toot my own horn but with a little reading I came up with this idea before I came back to see what solutions where posted.

You see I'm the kind of guy who likes things to be automated with my specific needs in mind,  This is why I chose to abandon Windows, but thats another thread.  I don't want to have to do any "preparation" to set up my desktop for the best possible configuration to play wow under, I just want it to do it.

seeing as how I just did a complete reinstall of Ubuntu I'm in the middle of the many lengthy WoW patch updates to testing isn't fast by any means.  This is the Script I'm trying.  Instead of  disabling Compiz-fusion,  I have may normal desktop environment set to the standard gnome-wm that we all see right after a fresh ubuntu install simply for testing purposes and will be switching to metacity while Wine is running the WoW Launcher.exe program, when wow is done,  It "should replace the metacity window manager with the gnome window manager.  The differences between the two are very subtle in appearance,  But with metacity,  it makes in possible to play in a truly windowed mode without any graphical glitching

```
#!/bin/bash
metacity --replace ; sleep 5 && env WINEPREFIX="/home/chris/.wine" wine "C:\World of Warcraft\Launcher.exe" ; sleep 5 && gnome-wm
```

Anyone see anything wrong that jumps out at them?  I'm still new to witting with bash.

---

### Post by ajgreeny on 2009-01-10
I think the semi colon should go after the sleep 5, if another script I use is correct, and it must be because it works.  This is basically the sort of thing I was suggesting, but didn't have time to test.

OK, I've just tested this and could not get it to work in this way for some reason, no matter where the semi colon was.  However, I already run a application called compiz switch to quickly turn compiz on and off with a single click and running this script:-

#!/bin/sh
compiz-switch && abiword && compiz-switch

with abiword as a test appliaction, worked brilliantly, so it can be done.  Get compiz switch from this site and it should work for you as well.
[http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

---

### Post by Dark Aspect on 2009-01-10
```
sudo apt-get install fusion-icon
```

Than go to System/Preferences/Sessions and add:

```
fusion-icon --no-start
```

Than the fusion-icon will load on start up, this way you can choose between compiz and metacity easily.

---

### Post by gettensome on 2009-01-10
heres one I'm testing and trying to debug at the moment, probably does the same thing,  but I want to learn shell scripting anyway, so take a look...

```
#!/bin/sh
IS_WOW_RUNNING='1'												# Test Viable to wait for user to exit game. 1 = running, 0 = not running
SERVICE='WoW'													# Wild card grep will scan for to check if wow is still running
														
metacity --replace && env WINEPREFIX="/home/chris/.wine" wine "C:\Program Files\World of Warcraft\Launcher.exe"	# Changes window manager to metacity to facilitate opperation

while [ $IS_WOW_RUNNING = yes ]; do 				# Begins checking for wow is list of processes 
								#
if [ ps ax | grep -v grep | grep $SERVICE > /dev/null ]; do	# Scanning for any process containing WoW in the name
	then							#
	$IS_WOW_RUNNING=1					# Found that WoW is running
	else							#
	compiz.real --replace --sm-disable --ignore-desktop-hints ccp --indirect-rendering  	# Resets Window Manager to original state 			
	$IS_WOW_RUNNING=0									# WoW no longer running, terminates while loop
fi
done
```

---

