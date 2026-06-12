---
title: "Screen resolution problem: xrandr failed to get size of gamma for output default"
date: 2016-03-27
forum: Virtualisation
---

### Post by enzo8 on 2016-03-27
Hi to all,

I installed ubuntu 15.10 as guest O.S. on virutalbox.

I have a problem with the screen resolution, I want set a resolution of 1024x768 but the max resolution that ubuntu return me is 800x600.

I tried to increase the max resolution to 1024x768 using the "XRANDR" command, but this command not work properly.

If I run the command I get the following error (**xrandr: Failed to get size of gamma for output default**):

```

user@Ubuntu:~$ xrandr --q
**xrandr: Failed to get size of gamma for output default**
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected primary 800x600+0+0 0mm x 0mm
   800x600       61.00  
   640x480       60.00

```

If I run the command for increase the screen resolution I get always the same error: [B]xrandr: Failed to get size of gamma for output default

[/B]Googling on the internet I not found any solution for this problem that work properly for me.

Please, can any one help me to resolve this problem?

Thanks in advance!

---

### Post by ajgreeny on 2016-03-27
I have moved this thread to the Virtualisation section where it may get better replies.

You probably needd to install the Guest Additions extension pack which you'll find at the VBox Download page
[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

Double click on the downloaded vbox-extpack file making sure it is the correct version for your VBox and it should automatically install in the VBox manager.

---

### Post by MAFoElffen on 2016-03-27
+1 on dl'ing the Extension Pack (previously there was the "Guest Additions ISO", but now replaced by this program extension). 

*** Ensure you download and install the correct version for what you have installed, *** Check "HELP" > "About" and note the version before downloading what you need.

After it downloads, if it does not autinstall ... (sometimes it does not) open the Download folder in Nautilus. Find the file and right-click on it. use "Open File With" and select "VirtualBox" It will intstall. If you have the incorrect version, it will tell you with an error during the attempted installation...

---

### Post by enzo8 on 2016-03-28
Thanks, with your suggestion I resolved the problem.

I installed the guest addition from the Virtual Box manager: "*Device --> Install guest addition*"

Thanks.

---

