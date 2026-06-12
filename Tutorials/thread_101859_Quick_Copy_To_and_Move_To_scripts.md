---
title: "Quick Copy To and Move To scripts"
date: 2005-12-10
forum: Tutorials
---

### Post by ardchoille on 2005-12-10
This how-to will show you how to have a fast way to copy or move a file from one directory to another in nautilus. I wrote these scripts because I had a "files" directory with 20 files in it and I needed each of the 20 files to go to 20 different locations. Rather than right-click a file, choose cut, surf to the target directory, right-click the, choose paste, go back to the source directory and repeat all of that for the remaining 19 files, I wrote some scripts that perform these steps much faster.

**Nautilus script explanation**
A nautilus script is just an executable shell script (usually bash) that is placed in a special scripts directory so that the Nautilus graphical shell can find it. This is a really neat function of Nautilus, because it allows you to extend the functionality the the file browser to do just about anything. Scripts are invoked by selecting a file or group of files, and right-clicking with the mouse, to bring up a 'Context' menu. One of the options of this menu is the 'Scripts' submenu (this option only appears once you have at least one script in the scripts directory), which allows you to select a script to invoke on the selected files.

For a script to appear on the script menu, it must:
1. be placed in your scripts directory (~/.gnome2/nautilus-scripts), and
2. be executable (with chmod a+x filename)

If you place an executable script in your scripts directory, its name will not necessarily appear on the scripts menu immediately. You first must visit the scripts directory with Nautilus - which can be done using the last option in the scripts menu. Once the directory is visited, Nautilus will know about which scripts you have, and you will be able to use them.

**Now, on to the Copy To and Move To scripts.**

**The Copy To script:**
Place the following code in a new file, give it a filename of copyto and make it executable with chmod a+x copyto. Move the new file to the ~/.gnome2/nautilus-scripts/ directory, open nautilus and you'll find a new right-click menu item entitled "Scripts" with a submenu that has an item that quickly copies a file to any directory you desire.

```

#! /bin/bash
location=`zenity --file-selection --directory --title="Select a directory"`
for arg
do
if [ -e $location/$arg ];then
   zenity --question --title="Conflict While Copying" --text="File "$location/$arg" already exists. Would you like to replace it?"
   case "$?" in
      1  )  exit 1 ;;
      0  )  cp $arg $location ;;
   esac
else
   cp $arg $location
fi
done

```

**The Move To script:**
Place the following code in a new file, give it a filename of moveto and make it executable with chmod a+x moveto. Move the new file to the ~/.gnome2/nautilus-scripts/ directory, open nautilus and you'll find a new right-click menu item entitled "Scripts" with a submenu that has an item that quickly moves a file to any directory you desire.

```

#! /bin/bash
location=`zenity --file-selection --directory --title="Select a directory"`
for arg
do
if [ -e $location/$arg ];then
   zenity --question --title="Conflict While Moving" --text="File "$location/$arg" already exists. Would you like to replace it?"
   case "$?" in
      1  )  exit 1 ;;
      0  )  mv $arg $location ;;
   esac
else
   mv $arg $location
fi
done

```

As you can see, nautilus scripts allow you to extend nautilus to do almost anything. I have put my entire Gnome Applications menu in my nautilus/desktop right-click menu so I don't even use my gnome menu much anymore.

For instance, you can put the below code into a new text file, give it a name of terminal or something like that, make it executable and move it to ~/.gnome2/nautilus-scripts/Terminals or ~/.gnome2/nautilus-scripts/Apps or whatever suits you, and you'll have a right-click menu item to open gnome-terminal. This can be done with any app, whether you need to use sudo or not.

```

#!/bin/sh
gnome-terminal


```

Basically, the "gnome-terminal" part of the above code is simply the cli command to start gnome terminal. You can use the gnome menu editor to find the proper commands for all the apps in the Applications menu.

 hope this how-to is of help to the community :)

More information, scripts and tutorials for nautilus scripts can be found [here]("http://g-scripts.sourceforge.net/").

---

### Post by anil_robo on 2005-12-14
Apparently most people read only the Desktop support forums. The same thread is a hit there! :D

---

### Post by moment on 2005-12-15
This is a great idea! I changed your code in order to handle files with space and also made it recursive and made it to show a progress bar while it's copying. The same can be implemented for "Move to" script I suppose.

Here is the code:
```

#! /bin/bash
location=`zenity --file-selection --directory --title="Select a directory"`
for arg
do
if [ -e "$location/$arg" ]; then
   zenity --question --title="Conflict While Copying" --text="File $location/$arg already exists. Would you like to replace it?"
   if [ "$?" = 1 ]; then
        exit 1
   fi
fi
   cp -R "$arg" "$location" &
   ORIG_SIZE=`du -bs "$arg"|awk '{print $1}'`
   CP_SIZE=`du -bs "$location/$arg"|awk '{print $1}'`

   (
        while [ $CP_SIZE -ne $ORIG_SIZE ]; do
        expr `expr $CP_SIZE \* 100` / $ORIG_SIZE
        CP_SIZE=`du -bs "$location/$arg"|awk '{print $1}'`
        done
        echo 100
   )| zenity --progress --auto-close --text "Copying \"$arg\"..."

done

```

---

### Post by ardchoille on 2005-12-15
> **moment]This is a great idea! I changed your code in order to handle files with space and also made it recursive and made it to show a progress bar while it's copying. The same can be implemented for "Move to" script I suppose.

Here is the code:
```

#! /bin/bash
location=`zenity --file-selection --directory --title="Select a directory"`
for arg
do
if [ -e "$location/$arg" ] said:**
> ; then
        exit 1
   fi
fi
   cp -R "$arg" "$location" &
   ORIG_SIZE=`du -bs "$arg"|awk '{print $1}'`
   CP_SIZE=`du -bs "$location/$arg"|awk '{print $1}'`

   (
        while [ $CP_SIZE -ne $ORIG_SIZE ]; do
        expr `expr $CP_SIZE \* 100` / $ORIG_SIZE
        CP_SIZE=`du -bs "$location/$arg"|awk '{print $1}'`
        done
        echo 100
   )| zenity --progress --auto-close --text "Copying \"$arg\"..."

done

```
Wow, thank you very much :)

---

### Post by linkunderscore on 2006-01-03
Awesome! These are very useful scripts. These should be implemented in future versions of nautilus by default--imo. :cool:

---

### Post by tonywhelan on 2007-10-17
> **moment said:**
> This is a great idea! I changed your code in order to handle files with space and also made it recursive and made it to show a progress bar while it's copying. The same can be implemented for "Move to" script I suppose.

Here is the code:
```

#! /bin/bash
location=`zenity --file-selection --directory --title="Select a directory"`
for arg
do
if [ -e "$location/$arg" ]; then
   zenity --question --title="Conflict While Copying" --text="File $location/$arg already exists. Would you like to replace it?"
   if [ "$?" = 1 ]; then
        exit 1
   fi
fi
   cp -R "$arg" "$location" &
   ORIG_SIZE=`du -bs "$arg"|awk '{print $1}'`
   CP_SIZE=`du -bs "$location/$arg"|awk '{print $1}'`

   (
        while [ $CP_SIZE -ne $ORIG_SIZE ]; do
        expr `expr $CP_SIZE \* 100` / $ORIG_SIZE
        CP_SIZE=`du -bs "$location/$arg"|awk '{print $1}'`
        done
        echo 100
   )| zenity --progress --auto-close --text "Copying \"$arg\"..."

done

```

I just found these scripts today (2 years after you posted it). I wrote a script myself some months ago to achieve this but mine was rather more long-winded (amateur programmer!). My version displayed the date, time, size of the files to be replaced to help the user make an informed decision, but that's easy to add to the script above. 

So I thought I'd try the script above and I feel there is one error in the code. If you select multiple files and are prompted whether or not to over-write an existing file, pressing "Cancel" exits the entire operation. I think it should just skip that one file and move on to the next. You can make the latter happen by replacing the "exit 1" with "continue"

Of course, if you were copying 20 files and they all existed at the destination already, you would be prompted 20 times about whether or not to overwrite. It would be nice if the user could be given the choice to "Overwrite, Overwrite All, Skip, Skip All" or similar but right now I'm not sure if zenity dialogs have that capability. 

cheers

---

### Post by flightless bird on 2007-11-09
These are absolutely fantastic, I agree they should be there from the word go. Not knowing zenity at all, how would the progress section be changed to display moving progress?

---

### Post by globalenigma on 2008-11-09
Thanks moment, I was looking for something like this for organizing a bunch of my pictures.  I wanted to move files I selected to a folder that did not exist.  I borrowed your code and modified it to prompt for a new folder name.  

```
#! /bin/bash
# Create a folder and move files to that folder
location=`zenity --entry --text "Enter folder name" --entry-text "New Folder"`
mkdir $location
for arg
do
if [ -e "$location/$arg" ]; then
zenity --question --title="Conflict While Copying" --text="File $location/$arg already exists. Would you like to replace it?"
if [ "$?" = 1 ]; then
exit 1
fi
fi
mv -f "$arg" "$location" &
ORIG_SIZE=`du -bs "$arg"|awk '{print $1}'`
MV_SIZE=`du -bs "$location/$arg"|awk '{print $1}'`

(
while [ $MV_SIZE -ne $ORIG_SIZE ]; do
expr `expr $MV_SIZE \* 100` / $ORIG_SIZE
MV_SIZE=`du -bs "$location/$arg"|awk '{print $1}'`
done
echo 100
)| zenity --progress --auto-close --text "Copying \"$arg\"..."

done

```


I wish I was better at codeing and could make it creat a folder from the filename excluding the numbers on the end.

ex.
pic01.jpg
pic10.jpg
pic100.jpg

when all those are selected a script that would make a folder called pic and move the files to it...

---

### Post by lambroger on 2011-04-27
In response to the guy that wanted overwrite, skip and cancel, I studied the zenity code and came up with following after testing for about 2 hours to make sure it worked properly. This is for the moveTo script, I implemented this on Maverick Meerkat Ubuntu 10.10.

```
#! /bin/bash
 location=`zenity --file-selection --directory --title="Select a directory"`
 for arg
 do
	 if [ -e "$location/$arg" ]; then
	 	#zenity --question --title="Conflict While Moving" --text="File $location/$arg already exists. Would you like to replace it?"
		ans=$(zenity --list --title="Conflict While Moving" --text="File $location/$arg already exists. What would you liked to do?" --radiolist --column "Pick" --column "Option" TRUE "Overwrite" FALSE "Skip" FALSE "Cancel")
	        case "$ans" in
			"Skip" ) 
				#zenity --info --title="skip executed" --text="$ans, hopefully that said Skip"
				zenity --info --title="Skip" --timeout=5 --text="Skipping moving $arg to $location!"
                                continue;;
			"Cancel" ) 
				#zenity --info --title="cancel executed" --text="$ans, hopefully that said Cancel"	
				zenity --info --title="Cancel" --timeout=5 --text="Canceling entire moving operation!"
				exit;; #this seems so brutal, is there a better way to do this?
			# We do not have to test for Overwite as that is default action with 'mv -f' below
		esac
	 fi
 	 mv -f "$arg" "$location" &
	 ORIG_SIZE=`du -bs "$arg"|awk '{print $1}'`
	 MV_SIZE=`du -bs "$location/$arg"|awk '{print $1}'`

	 (
		 while [ $MV_SIZE -ne $ORIG_SIZE ]; do
			 expr `expr $CP_SIZE \* 100` / $ORIG_SIZE
			 MV_SIZE=`du -bs "$location/$arg"|awk '{print $1}'`
		 done
		 echo 100
	 )| zenity --progress --auto-close --text "Moving \"$arg\"..."

 done

```

---

### Post by lambroger on 2011-04-27
Since coding moveTo was easy to do as far as overwriting and skipping are concerned, I have implemented this for CopyTo as well, along with information dialog boxes for skipping and canceling.

```
#! /bin/bash
 location=`zenity --file-selection --directory --title="Select a directory"`
 for arg
 do
	 if [ -e "$location/$arg" ]; then
		ans=$(zenity --list --title="Conflict While Copying" --text="File $location/$arg already exists. What would you liked to do?" --radiolist --column "Pick" --column "Option" TRUE "Overwrite" FALSE "Skip" FALSE "Cancel")
	        case "$ans" in
			"Skip" ) 
				#zenity --info --title="skip executed" --text="$ans, hopefully that said Skip"
				zenity --info --title="Skip" --timeout=5 --text="Skipping copying $arg to $location!"
				continue;;
			"Cancel" ) 
				#zenity --info --title="cancel executed" --text="$ans, hopefully that said Cancel"
				zenity --info --title="Cancel" --timeout=5 --text="Canceling entire operation!"	
				exit;; #this seems so brutal, is there a better way to do this?
			# We do not have to test for Overwite as that is default action with 'cp -Rf' below
		esac
	 fi
	 cp -Rf "$arg" "$location" &
	 ORIG_SIZE=`du -bs "$arg"|awk '{print $1}'`
	 CP_SIZE=`du -bs "$location/$arg"|awk '{print $1}'`

	 (
		 while [ $CP_SIZE -ne $ORIG_SIZE ]; do
			 expr `expr $CP_SIZE \* 100` / $ORIG_SIZE
			 CP_SIZE=`du -bs "$location/$arg"|awk '{print $1}'`
		 done
		 echo 100
	 )| zenity --progress --auto-close --text "Copying \"$arg\"..."

 done
```

---

### Post by tonywhelan on 2011-04-28
> **lambroger said:**
> Since coding moveTo was easy to do as far as overwriting and skipping are concerned, I have implemented this for CopyTo as well, along with information dialog boxes for skipping and canceling.



Thanks lambroger, I will try these out over the next few days when I get some free time

---

### Post by bmfc187 on 2011-11-26
@lambroger i tried these scripts on lucid and they do not work, the directory selection comes up but then when i select a directory it freaks out and closes, no files are copied/moved, and if i run it in terminal it just closes the terminal with no error message.  any idea what might be causing it not to work for me?

---

