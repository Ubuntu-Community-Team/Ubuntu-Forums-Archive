---
title: "Got a question...."
date: 2010-10-21
forum: Wine
---

### Post by masterskop on 2010-10-21
Hi,

How could I find out through a terminal what the full length of a command is when I run a program from the Application's menu?  If I have installed Battlefield 2 in wine and run it from the drop down menu on the desktop, I can get the game to run.  But, when I open a command line box (alt + F2) and type in padsp wine "C:\Program Files\EA GAMES\Battlefield 2\BF2.exe" ... nothing works.  I have setup the wine config correctly.  But, why does BF2 work from a drop down under apps and not through a command via terminal?  So, how can I find out what the command line is from the drop down menu under Wine within the Applications menu?

I have found the BF2 and BF2 special forces are in the drop down menu.  But, when I added the HardJustice mod, it doesn't apprear in the drop down menu.  How can I add the HardJustice mod like BF2 special forces? <---- this is where I would like to learn about the command lines :)

Any and all help is appreciated!

---

### Post by lykeion on 2010-10-21
Rightclick BF2 icon in applications menu > Add launcher to desktop
Rightclick launcher on desktop > Properties
The launch command is displayed in the Command textfield

To manually create entries in the applications menu:
Rightclick applications menu > Edit menus
Select where to create the new item on left
Click New Item on right and enter Name and Command
(you can also set an icon by clicking on the icon on the left.

Hope this helps...

PS Instead of using ALT+F2 to launch commands, try opening a Terminal (Applications menu > Accessories > Terminal) and enter the command from there. That way you get feedback if the command failed.

---

