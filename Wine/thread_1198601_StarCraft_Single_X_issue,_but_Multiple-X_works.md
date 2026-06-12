---
title: "StarCraft Single X issue, but Multiple-X works ?"
date: 2009-06-27
forum: Wine
---

### Post by Sugi on 2009-06-27
Oh kay, So I compiled wine 1.1.23 and ran StarCraft while I had separate X running, but now when I run only a single X at a time Starcraft won't scale to fit my monitor.  Any ideas on how to fix this?

I have tried adding a line to my xorg, but this did not fix the issue.

RE: from APPDB
> It's just NVidia's driver being too smart or lenovo's LCD being wrong.

You have to disable horizontal and vertical mode checking.

So, for my /etc/X11/xorg.conf in the "Screen" section, I had to add the following line:

Option "ModeValidation" "NoVertRefreshCheck,NoHorizSyncCheck"

By the way, I have the exact same machine.

My "Screen" section:
Section "Screen"
Identifier "screen0"
Device "nvidia0"
Monitor "ThinkPad T61 TFT"
DefaultDepth 24
Option "TwinView" "0"
Option "TwinViewXineramaInfoOrder" "DFP-0"
Option "ModeValidation" "NoVertRefreshCheck,NoHorizSyncCheck"
Option "metamodes" "DFP: 1440x900 +0+0"
SubSection "Display"
Depth 8
EndSubSection
SubSection "Display"
Depth 16
EndSubSection
SubSection "Display"
Depth 24
EndSubSection
EndSection
[URL="http://appdb.winehq.org/objectManager.php?sClass=version&
iId=149"]http://appdb.winehq.org/objectManager.php?sClass=version&iId=149[/URL]

I have also tried setting up my xorg to run a X specially for starcraft, but I couldn't get it to work. :/
[http://ubuntuforums.org/showthread.php?p=5144003](http://ubuntuforums.org/showthread.php?p=5144003)

I was wondering if anyone had a fix for this 

OR OR 

if they had a script that kept the mouse from leaving that X during video games.  It was floating around on Ubuntu forums and the net.  This scripts will not allow the mouse to leave a twinview or separate X setup on dual monitors.  This would be helpful to me, because that means I can keep my dual-setup display while playing games in wine.

Specs:
 ~ Working:
Compiled Wine 1.1.23
Dual Display Separate X 
Display 0 = 1680x1050
Display 1 = 1920x1080
Display 1 runs StarCraft

StarCraft works on this setup and will scale and stretch to fix the Display 1, BUT I can not play like this because my mouse moves over to DISPLAY 0 while I tried to view areas in StarCraft.  Very annoying.

~ Not Working:
Same Compiled Wine 1.1.23
Single Display on the 1920x1080

StarCraft loads up, but does not scale and stretch to fit the display.
Like this image: [IMG]http://img13.imageshack.us/img13/7905/screenshotopv.png[/IMG]
NOTE: This is not my image, but the same problem as mine.

Thank you for your time,
Sugi

---

### Post by Sugi on 2009-06-27
[http://ubuntuforums.org/showthread.php?p=7529125#post7529125](http://ubuntuforums.org/showthread.php?p=7529125#post7529125)

Sugi

---

