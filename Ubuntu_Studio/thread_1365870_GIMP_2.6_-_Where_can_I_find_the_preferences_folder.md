---
title: "GIMP 2.6 - Where can I find the preferences folder?"
date: 2009-12-27
forum: Ubuntu Studio
---

### Post by RockOut on 2009-12-27
I am looking to delete the preferences folder, in an attempt to fix a problem with GIMP I am having ([http://ubuntuforums.org/showthread.php?t=1013580](http://ubuntuforums.org/showthread.php?t=1013580)) . The original problem is that I cannot edit anything in GIMP using any tool whatsoever. To save you a click, the solution that seemed to work for another person this this issue was to delete the Preferences folder for GIMP. That user was on GIMP 2.4; I am on 2.6 -- though, I think the same solution may work for me as well. I'm on Karmic.

I cannot find this folder to delete it! I have searched the GIMP folder under usr/share/gimp/2.0 , though this directory looks like it's for plugins, textures, and GIMP tools, not the Preferences folder.

Am I looking for the wrong folder? I have also opened GIMP and gone to Edit>Preferences to see if the solution was to change a setting there in the "Folders" section, and came up empty.

---

### Post by howefield on 2009-12-27
Have you tried your home folder ?

Places  > Home Folder and press alt + H to view the hidden folder .gimp-2.6

---

### Post by RockOut on 2009-12-28
I just gave that a try... CTRL + H in my Home folder **did** reveal the hidden files and file folders. Yay! Thanks! I will remember this tip!

No Preferences folder found, though. Should I be looking elsewhere?

---

### Post by Paszt on 2010-06-18
[FONT=Arial][SIZE=2]I know this is old, but in case someone else is searching as was I:[/SIZE][/FONT]

GIMP 2.6 preferences are stored in a file called [FONT=Courier New]      gimprc[/FONT] in your personal GIMP directory.
path: [FONT=Courier New]/home/<userName>/.gimp-2.6/gimprc

[FONT=Arial][SIZE=2]Deleting [FONT=Courier New]gimprc[/FONT] didn't correct the problem for me; deleting [/SIZE][/FONT][/FONT][FONT=Courier New][SIZE=2]devicerc[/SIZE][/FONT][FONT=Courier New][FONT=Arial][SIZE=2] (renaming actually) did however.  If saving all the GIMP preferences isn't a concern, it should be safe to delete all the files ending in [FONT=Courier New]rc[/FONT] in the above mentioned folder.[/SIZE][/FONT]
[/FONT]

---

