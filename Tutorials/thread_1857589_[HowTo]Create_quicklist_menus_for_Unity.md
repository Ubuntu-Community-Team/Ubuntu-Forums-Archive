---
title: "[HowTo:]Create quicklist menus for Unity"
date: 2011-10-10
forum: Tutorials
---

### Post by JRV on 2011-10-10
The thing I miss most in unity is a menuing system.  This tutorial will explain how to create an icon in the launcher bar on the left side of the screen.  A right click on this icon will display a quicklist menu.  If you left click the icon you will get a message telling you to right click. You can use a quicklist to group together any number on actions, so you don't have too many icons in the launcher.  

First create the message telling you to right click.

Copy this text to a file called "r-click.sh" in your home directory:
```

#!/bin/sh

g=`zenity --title="  " --info --text="Right Click For Menu" --height=100 --width=250 --timeout=1`

exit 0

```
Now open a terminal and make it executable with the command:
```

chmod +x r-click.sh

```
Or you can right click on the file in nautilus, select properties=>permissions, and check the executable box.

While you are in the terminal test the script with the command:
```

./r-click.sh

```
You should see a window open on the screen telling you to right click, and it will disappear in one second.


The only kind of file that can have an icon in the launcher bar is a .desktop file.  
There are a few things you need to know about .desktop files, they can behave rather strangely.
[LIST]
[*] The name can appear differently depending on whether the executable flag is set or clear.

[*] The name can be different in nautilus than it is in the terminal.

[*] The icon displays differently depending on whether the executable flag set or clear.
[/LIST]
(I will explain how to keep the name straight after we create the .desktop file.)
[LIST]
[*] You can not double click on it to edit a .desktop file.

[*] To edit it you can call the editor from the command line.  (gedit whatever.desktop)

[*] You can also open gedit and then open it through the file menu.
[*] The application icons in the dash are desktop files.  They are located in /usr/share/applications.
[/list]


The normal place to store your .desktop files is in /home/USER_NAME/.local/share/applications.  You will want to move the file here when you are done editing it, but we will create it in your home directory to make editing easier.  (Gedit can not see into hidden directories.)

Create a empty file in your home directory named "Sample Menu" and copy the following code into it:
```

#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=administration
Name[en_US]=Sample Menu
Exec=/home/USER_NAME/r-click.sh
Name=Sample Menu
Icon=administration

X-Ayatana-Desktop-Shortcuts=Calculator;Nautilus as Root;System Monitor;Take Screenshot

[Calculator Shortcut Group]
Name=Calculator
Exec=/usr/bin/gcalctool
TargetEnvironment=Unity

[Nautilus as Root Shortcut Group]
Name=Nautilus as Root
Exec=gksudo nautilus
TargetEnvironment=Unity

[System Monitor Shortcut Group]
Name=System Monitor
Exec=gnome-system-monitor
TargetEnvironment=Unity

[Take Screenshot Shortcut Group]
Name=Take Screenshot
Exec=gnome-screenshot --interactive
TargetEnvironment=Unity

```

At this point it is not a .desktop file, so double click on it to edit it.

Find the line that says "Exec=/home/USER_NAME/r-click.sh" and change USER_NAME to your user name.

In nautilus right click on the file and rename it "Sample Menu.desktop".

Open a terminal and make it executable with the command:
```

chmod +x "Sample Menu.desktop"

```
Or you can right click on the file in nautilus, select properties=>permissions, and check the executable box.


When you drag this icon to the launcher bar you will have a working menu.

As I mentioned earlier names of .desktop files can be confusing.  The way to keep them straight is to keep the name identical in the "Name[en_US]=" line, the "Name=" line, and the name to the left of .desktop.

Next question, how would you add an application to the menu?

Suppose you want to add the AisleRiot Solitaire collection to your menu.

First you would need to find the command to execute the program. It is not aisleriot.  A lot of programs are named one thing with the command to run it named something different.  To find the correct command we will need to look at the properties of the application's .desktop file.  If an installed program does not have a .desktop file you can often find the command by following the link to the program in Software Center.  Sometimes you will have to Google it.

In nautilus navigate to the /usr/share/applications directory.

Locate the AisleRiot Solitaire icon, right click it, and select properties.  The "Command:" line tells you the proper command to run the program.  In this case it is:
```

/usr/games/sol

```

Now edit the .desktop file with the command:
```

gedit "Sample Menu.desktop"

```
Or you can start gedit and use it's "Open" button to find the file.
Look for the line that reads:
```

X-Ayatana-Desktop-Shortcuts=Calculator;Nautilus as Root;System Monitor;Take Screenshot

```
and add
```

;Aisleriot Solitaire

```
The line should read:
```

X-Ayatana-Desktop-Shortcuts=Calculator;Nautilus as Root;System Monitor;Take Screenshot;Aisleriot Solitaire

```
That will make the selection appear on the menu.
Now add the code to run the program:
```

[Aisleriot Solitaire Shortcut Group]
Name=Aisleriot Solitaire
Exec=/usr/games/sol
TargetEnvironment=Unity

```


Tested in Ubuntu 11.10 beta on Monday 10/10/11.

These are threads I started in the process of learning how to use .desktop files:

[http://ubuntuforums.org/showthread.php?t=1700605](http://ubuntuforums.org/showthread.php?t=1700605)
[http://ubuntuforums.org/showthread.php?t=1701240](http://ubuntuforums.org/showthread.php?t=1701240)
[http://ubuntuforums.org/showthread.php?t=1706383](http://ubuntuforums.org/showthread.php?t=1706383)

You may find usefull information in them.

---

