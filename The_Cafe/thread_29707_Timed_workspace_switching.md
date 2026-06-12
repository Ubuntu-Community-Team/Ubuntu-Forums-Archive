---
title: "Timed workspace switching"
date: 2005-04-25
forum: The Cafe
---

### Post by MBrown06 on 2005-04-25
Do anyone know of a way to switch linux workspaces on a timer? I have a Linux box I use to monitor various network management tools, and want to have a different tool run on each workspace. I want the monitor to be mounted on a wall and then toggle through the workspaces about every 15 seconds. I know this can be done through keyboard commands, but I need to to be automated.

Any help would be greatly appreciated.

---

### Post by sas on 2005-04-25
[QUOTE=MBrown06]Do anyone know of a way to switch linux workspaces on a timer? I have a Linux box I use to monitor various network management tools, and want to have a different tool run on each workspace. I want the monitor to be mounted on a wall and then toggle through the workspaces about every 15 seconds. I know this can be done through keyboard commands, but I need to to be automated.

Any help would be greatly appreciated.[/QUOTE]
 if by keyboard commands you mean command line interface you could stick the commands in a shell script.....

---

### Post by Nis on 2005-04-25
You could use 3ddesktop.  It has a command line switch --gotoright (and --gotoleft, --gotoup, --gotodown).  You would just have to do some tweaking of the 3ddesktop configuration so it would run well on your machine and then setup a cron job to run '3ddesk --gotoright' every so often.

---

### Post by MBrown06 on 2005-04-25
The "keyboard commands" are "crtl" + "shift" + "1" from the desktop. I have not looked at 3ddesktop yet, so I will download that and take a look.

Thanks alot.

---

