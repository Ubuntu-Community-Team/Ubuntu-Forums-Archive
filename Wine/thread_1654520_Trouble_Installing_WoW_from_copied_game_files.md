---
title: "Trouble Installing WoW from copied game files"
date: 2010-12-28
forum: Wine
---

### Post by danielgrosvenor on 2010-12-28
I'm having some trouble installing World of Warcraft.  I downloaded the game to my Windows PC and so have no installation disks, and I have a 512 connection so re-downloading 20+ gig is out of the question.  So I did the only logical thing I could think of and copied my entire World of Warcraft directory to an external HDD, and pasted it into */home/dan/.wine/dosdevices/c:/Program Files*

Now I'm able to get the game to run by opening Terminal and entering:
```
wine "C:\\Program Files\\World of Warcraft\\WoW.exe"
```but I'd ideally like to have my laptop see WoW as being "installed", so I just need to click on a shortcut rather than having to dive into Terminal every time I want to open the game up.  I tried manually adding a shortcut in the Games folder to */home/dan/.wine/dosdevices/c:/Program Files/World of Warcraft/Wow.exe* but I got a 'failed to execute child process' message.

It was at this point that I installed [CrossOver Games]("http://www.codeweavers.com/products/cxgames/").  When I try to install it from the Install Windows Software menu, it prompts me to install an Installer File or an Installer Folder.  I chose Folder and pointed it to *.wine/drive_c/Program Files/World of Warcraft* but this doesn't work.  The install starts to do something, then says:
```
[B]
An error occurred while running the 'AIEInsertMedia(World of Warcraft)' task[/B]

This disk contains two sections, one for Mac and one for Windows.  In order for CrossOver to use this disk it must be mounted so that the Windows portion is visible.

To make this change, remount as root with this command:
mount -t udf -o users,ro,unhide,uid=1000 /dev/cdrom "/home/dan/.wine/drive_c/Program Files/World of Warcraft"
```I tried adding 'sudo' and typing this command into Terminal, but nothing seems to happen.

erm... help?!  :sad:

---

### Post by disabledaccount on 2010-12-28
First of all I always create prefixes for each application. Although new wine versions supports "profiles", **prefixes** are still the most powerfull way for managing/moving/making backups/creating special "windows" environments for particular apps - you should learn about how to use them.

In this case I suggest to create shell script file with that working line inside.
Then You can create launcher with command like this: bash /home/usrername/.wine/yourapp_launching_script.sh

What this is for?
D2 MedianXL launching script from my laptop (very old one ;) )
> #!/bin/bash
export WINEPREFIX='/home/usrdata/wine-d2-median'
**export WINEDEBUG=-all**
cd /home/usrdata/wine-d2-median
wine 'c:/Diablo2/Diablo II.exe'
#schedtool -a 0x2 -n 2 -e wine 'c:/Diablo2/Diablo II.exe'
exit 0
So You can: disable debugging, what speeds things up a bit and set CPU affinity what protects some games from going crazy on multi-core platforms ;)
For some apps this is also important to change current path.

Have a nice play... :)

...and I hope that was 'slow' enough...

---

### Post by danielgrosvenor on 2011-01-01
Hi

Thanks for your advice, but I'm a little unclear about how to go about creating this shell script.  Is this something I can do simply through typing something into Terminal?  :? #n00b

---

### Post by disabledaccount on 2011-01-01
Shell script is just text file with shell commands inside.
So You can create file with text editor like **gedit**, give it *.sh extension and set executable flag (by right clicking on it -> properties -> permissions -> "Allow executing file as programm")
File can contain any number of shell comands, what allows you to set wine variables, niceness (priority), CPU affinity and many other things - like setting gamma for display, setting GPU clocks (not every game needs full power), change gfx FAA, AF, Vsync, etc.
It is good practice to place so called "shebang" in first line: **#!/bin/bash** - this indicates that file contains script and tells which interpreter should be used.

---

### Post by Tweak42 on 2011-01-04
The Crossover error you are getting is because it's thinking you are installing from cd/dvd and is looking for the installer files.  

You will have to ask the codeweaver guys if there is an installer option to setup a existing install, but from my experience with Crossover 8 (current is 9) it was not possible.  That isn't to say you can't just plop the game directory in a clean bottle and create the desktop icon manually, which was what I did by installing another program, examining the created icon and making my own icon.

Crossover is good for managing MS Office and keeping programs separate in their own "bottles", but for just Wow I found I could get by with the latest wine and manually installing and configuring.  Thankfully wine can handle the Launcher.exe for patches and Repair.exe for damaged files so keep a backup of the game directory around in case you need to nuke and reinstall.

---

### Post by danielgrosvenor on 2011-01-04
Yeah, I like the idea of buying Crossover because I know the money goes to a good cause, but for now it's not quite what I want.  All I'm after is something let me run Steam games and WoW -- and considering half my Steam games don't run through Steam directly (I need to find the .exe files and open them up using WINE) I think I'll just stick with WINE for the time being.

---

