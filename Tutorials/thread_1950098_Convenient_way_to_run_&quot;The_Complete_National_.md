---
title: "Convenient way to run &quot;The Complete National Geographic) set"
date: 2012-03-31
forum: Tutorials
---

### Post by Mahkoe on 2012-03-31
A while ago I went and got the complete National Geographic, every issue since 1888. This is what I do to run it so I don't have to keep switching the CDs:

**Step 1:** Install playonlinux. It's available in the Ubuntu Software Center, and at [http://playonlinux.net](http://playonlinux.net). Then, open it and hit "Install". Near the bottom left of the window that opens, it says "Install a non-listed program". You'll want to click that. Then, follow these steps to go through the wizard:

1a) Select "Install a program in a new virtual drive" and hit Next
1b) Type any name you like and hit Next. Make sure you write this name down
1c) Check "Install some libraries" and hit Next
1d) Check off "POL_Install_Adobe-Air" and hit Next
1e) Pop in CD #1 from the set and in the Playonlinux wizard, browse to the executable on the disc called "CGN-1.12-windows-installer.exe".
1f) Install the program normally. NOTE: If it gets stuck on "Installing adobe air" or something similar to that, simply hit cancel, then hit cancel in the wizard, restart the whole installation, and make sure you use the same name for step 1c). DO NOT CHECK OFF "Run the Complete National Geographic" in the installer. It will bork everything.
1g) In the windows that opens next, click on "The Complete National Geographic.exe", then hit next and type in a name for it. Hit next, select "I don't want to make another shortcut" from the list, and hit next. You're done! Well, not quite.. 

**Step 2:** Create a folder in your home folder called ".ng". In this folder, create 6 folders ("d1","d2","d3","d4","d5", and "d6") This will be the longest process, but I promise it's worth it; copy all the files from disc 1 into the d1 folder, all the files from disc 2 in the d2 foler, etc. Right click on the "d6" folder and hit make link. Rename the link to "disk". Create a document called ".position", open it in the text editor, and type in "1" (without the quotes) and save it. Finally, create a file called ".switch.sh". open it your text editor, and paste in the following code MAKING SURE TO RENAME ALL THE FOLDER LOCATIONS APPROPRIATELY:

```

#!/bin/bash

#This script reads a document called .position, and symlinks
#a folder (/home/yourUsername/.ng/disk) to the appropriate disc
#files copied earlier. 

#You only need to rename the following 8 locations
d1="/home/yourUsername/.ng/d1"
d2="/home/yourUsername/.ng/d2"
d3="/home/yourUsername/.ng/d3"
d4="/home/yourUsername/.ng/d4"
d5="/home/yourUsername/.ng/d5"
d6="/home/yourUsername/.ng/d6"
disk="/home/yourUsername/.ng/disk"
pos="/home/yourUsername/.ng/.position"
#After this comment, nothing else needs to be changed

if [ "`cat $pos`" = "1" ]; then
	rm $disk
	ln -s $d1 $disk
	echo $(expr $(cat $pos) + 1) > $pos
	xmessage -timeout 1 "Disc 1 is loaded"

elif [ "`cat $pos`" = "2" ]; then
	rm $disk
	ln -s $d2 $disk
	echo $(expr $(cat $pos) + 1) > $pos
	xmessage -timeout 1 "Disc 2 is loaded"

elif [ "`cat $pos`" = "3" ]; then
	rm $disk
	ln -s $d3 $disk
	echo $(expr $(cat $pos) + 1) > $pos
	xmessage -timeout 1 "Disc 3 is loaded"

elif [ "`cat $pos`" = "4" ]; then
	rm $disk
	ln -s $d4 $disk
	echo $(expr $(cat $pos) + 1) > $pos
	xmessage -timeout 1 "Disc 4 is loaded"

elif [ "`cat $pos`" = "5" ]; then
	rm $disk
	ln -s $d5 $disk
	echo $(expr $(cat $pos) + 1) > $pos
	xmessage -timeout 1 "Disc 5 is loaded"

elif [ "`cat $pos`" = "6" ]; then
	rm $disk
	ln -s $d6 $disk
	echo $(expr $(cat $pos) + 1) > $pos
	xmessage -timeout 1 "Disc 6 is loaded"

fi

if [ "`cat $pos`" = "7" ];
	then
		echo 1 > $pos
fi

```

Finally, right click on .switch.sh, click properties, go to Permissions, and check off "allow executing file as program".

**Step 3**: Go into playonlinux select the national geographic entry, and hit configure. Click the tab at the top labeled "Wine", then hit "configure wine". In the window that opens, hit the tab labeled "Drives", make a new drive, and in the part where it asks for a location, put the location of the symlinked folder (if you used my suggested folder names, it will be "/home/yourUsername/.ng/disk"), and hit apply. Close the wine configuration window and the playonlinux configuration window. You're done! Except for...

**BONUS STEP**: Make a launcher on your panel that will run .switch.sh

Pre-11.04 instructions: Right-click on your panel, hit "Add to Panel..." then hit "Custom application launcher". Where it says "Command" type in the location of .switch.sh (if you used my suggested file names, it will be "/home/yourUsername/.ng/.switch.sh"). You can click on the rocket icon in that same window and select an icon to display (most are found in /usr/share/icons)

Post-11.04 instructions:
Right-click on your desktop, and hit make launcher. Enter the location of the bash script (if you used my suggested file names, it will be "/home/yourUsername/.ng/.switch.sh"))

Okay, now you're done.

---

