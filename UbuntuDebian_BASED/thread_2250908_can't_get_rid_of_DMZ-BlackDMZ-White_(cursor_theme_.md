---
title: "can't get rid of DMZ-Black/DMZ-White (cursor theme problem)"
date: 2014-10-31
forum: Ubuntu/Debian BASED
---

### Post by hasanaa on 2014-10-31
i tried all solution on forum but couldnt get rid of DMZ cursor theme. 
i copied the new cursor theme to /usr/share/icons/, changed on dconf editor and did the *update-alternatives* stuff (added new entry etc.) still have DMZ on my desktop. 
i even deleted DMZ-Black/DMZ-White from /usr/share/icons/ but that crazy crap doesnt give up!! 
PLS help

---

### Post by CantankRus on 2014-11-01
Have you logged out and back in?
Can you link to the cursor theme you are trying to install?
I have an Elementary Luna iso I can test on.

---

### Post by hasanaa on 2014-11-01
i did. log out/in and restart.

[simpleandsoft]("http://gnome-look.org/content/show.php/Simple+and+Soft?content=28427") and [ecliz]("http://gnome-look.org/content/show.php/Ecliz?content=110340")

---

### Post by CantankRus on 2014-11-01
> **hasanaa said:**
> i did. log out/in and restart.

[simpleandsoft]("http://gnome-look.org/content/show.php/Simple+and+Soft?content=28427") and [ecliz]("http://gnome-look.org/content/show.php/Ecliz?content=110340")
Those themes do not have **cursor.theme** files which are needed for alternatives.
Did you create them?

---

### Post by hasanaa on 2014-11-01
i did

---

### Post by CantankRus on 2014-11-01
OK what is your terminal output for...
```
gsettings get org.gnome.desktop.interface cursor-theme
```
and
```
update-alternatives --display x-cursor-theme
```

eg my output...
```
[COLOR="#008000"]glen@Luna:~$[/COLOR] **gsettings get org.gnome.desktop.interface cursor-theme**
'DMZ-Black'

[COLOR="#008000"]glen@Luna:~$[/COLOR] **update-alternatives --display x-cursor-theme**
x-cursor-theme - manual mode
  [COLOR="#FF0000"]link currently points to /usr/share/icons/DMZ-Black/cursor.theme[/COLOR]
/etc/X11/cursors/core.theme - priority 30
/etc/X11/cursors/handhelds.theme - priority 20
/etc/X11/cursors/redglass.theme - priority 20
/etc/X11/cursors/whiteglass.theme - priority 20
/usr/share/icons/DMZ-Black/cursor.theme - priority 20
/usr/share/icons/DMZ-White/cursor.theme - priority 90
/usr/share/icons/XenonBlue/cursor.theme - priority 20
/usr/share/icons/XenonBlue32/cursor.theme - priority 20
Current 'best' version is '/usr/share/icons/DMZ-White/cursor.theme'.
```

and 
```
cat /usr/share/icons/Ecliz/cursor.theme
```
Should show...
```
[COLOR="#008000"]glen@Luna:~$[/COLOR] **cat /usr/share/icons/Ecliz/cursor.theme**
[Icon Theme]
Inherits=[COLOR="#FF0000"]Ecliz[/COLOR]
```

---

### Post by hasanaa on 2014-11-01
```
~$ gsettings get org.gnome.desktop.interface cursor-theme
'simpleandsoft'
```

```
~$ update-alternatives --display x-cursor-theme
x-cursor-theme - manual mode
  link currently points to /usr/share/icons/simpleandsoft/cursor.theme
/etc/X11/cursors/core.theme - priority 20
/etc/X11/cursors/handhelds.theme - priority 20
/etc/X11/cursors/redglass.theme - priority 20
/etc/X11/cursors/whiteglass.theme - priority 20
/usr/share/icons/simpleandsoft/cursor.theme - priority 51
Current 'best' version is '/usr/share/icons/simpleandsoft/cursor.theme'.
```

```
~$ cat /usr/share/icons/simpleandsoft/cursor.theme
[Icon Theme]
Inherits=simpleandsoft
```

---

### Post by CantankRus on 2014-11-01
All looks ok.
I created a cursor.theme file for **simpleandsoft** and installed in Luna and works fine.
In your efforts to get working did you run any other commands like **sudo ln [COLOR="#808080"]<blahblah>[/COLOR]** ?

I use this script to change cursors. Try if you like.
All it needs is the cursor theme be placed in **/usr/share/icons** and contain a cursor.theme file.
Save as **change_cursor.sh** and make executable.
```
#!/bin/bash

####################################################################
##                                                                ##
##     Script to change cursors. Only lists themes installed to   ##
##     /usr/share/icons.                                          ##
##     Theme must have a cursor.theme file                        ##
##                                                                ##
####################################################################

####################################################################
##                                                                ##
##     To change the cursor theme, the script will                ##
##	1) Change dconf setting                                   ##
##	2) Register the theme with update-alternatives            ##
##	3} Select the theme in update-alternatives                ##
##                                                                ##
##     To change the cursor size the script will                  ##
##	1) Change dconf setting                                   ##
##	2) Edit the ~/.Xresources file or create if               ##
##         it doesn't exist                                       ##
##                                                                ##
##      ....................................                      ##
##      :   Tested in Ubuntu Raring 13.04  :                      ##
##      :..................................:                      ##
####################################################################

CURRENTSIZE=$(gsettings get org.gnome.desktop.interface cursor-size)
THEME=$(gsettings get org.gnome.desktop.interface cursor-theme)
touch ~/.Xresources

## create installed cursor list text file
#ls -R /usr/share/icons | grep "\/cursors:" | sed -e 's/\/cursors://g' -e 's/\/usr\/share\/icons\///g' > ~/.cursorlist.txt
find /usr/share/icons -name "cursor.theme" | cut -f 5 -d '/' | sort > ~/.cursorlist.txt
echo -e "\n\033[36mYour current cursor theme is \033[0m$THEME \033[36m"

 
## show a numbered list of cursors to choose from
cat -b ~/.cursorlist.txt 
totalthemes=$(wc -l ~/.cursorlist.txt | awk '{print $1}') 

	echo -e "\033[36mEnter your new theme selection number:\033[0m"
	read CHOICE


## match the theme selection number to the cursor name
CURSOR=$(cat ~/.cursorlist.txt | sed -n $CHOICE'p') 
	echo -e "\n\033[36mYou have selected \033[0m$CURSOR\n\033[36mContinue?(Y/n):\033[0m"
	read Ans
if [[ $Ans == "y" || $Ans == "Y" || $Ans == "yes" || $Ans == "Yes" || $Ans == "" ]]
  then
    echo -e "\n\033[36mUsing update-alternatives requires Authentication of Admin privileges...\033[0m"
  else
    echo -e "\nYou chose not to continue...\n"
	echo -e "\n\033[36mYour current cursor theme is \033[0m$THEME \033[36m"
	read -n 1 -p "Press any key to exit this script..."
exit
fi


## Change to selected  cursor
	gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" &
	sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme 20 & wait;
	sudo update-alternatives --set x-cursor-theme /usr/share/icons/$CURSOR/cursor.theme &
	#sudo sh -c "echo '[Icon Theme]\nInherits=$CURSOR' > /usr/share/icons/DMZ-White/cursor.theme"
wait;


## Set size of cursor
CURRENTSIZE=$(gsettings get org.gnome.desktop.interface cursor-size)
	echo -e "\n\033[36mYour current cursor size is \033[0m$CURRENTSIZE \n\033[36mWould you like to change the size?(Y/n):\033[0m"
	read Ans
if [[ $Ans == "y" || $Ans == "Y" || $Ans == "yes" || $Ans == "Yes" || $Ans == "" ]]
  then
    echo  
  else
    echo -e "\nYou chose not to continue..." 

## writes to or creates a ~/.Xresources file to reflect curent cursor size. Need to do this when choosing not to change size and ~/.Xresources doesn't exist
	echo -e "\n\033[36mYou have enabled the \033[0m$CURSOR \033[36mcursor theme with size unchanged of \033[0m$CURRENTSIZE\033[36m \nYou need to log out to complete the change:\033[0m";
		if grep "Xcursor.size:" ~/.Xresources > /dev/null; then
			#echo "Xcursor.size line exists"
			sed -i "/Xcursor.size/c\Xcursor.size:${CURRENTSIZE}" ~/.Xresources
		else
			#echo "Xcursor.size line does not exist"
			echo "Xcursor.size:${CURRENTSIZE}" >> ~/.Xresources
		fi
	read -n 1 -p "Press any key to exit this script..."
exit
fi

## Choose size
	echo -e "\033[36mChoose your new cursor-size from 16, 24, 32, 48, or 64\033[36m"
	read SIZE

## Confirm choice
	echo -e "\n\033[36mYou have selected a cursor size of \033[0m$SIZE\nContinue?(Y/n):"
	read Ans
if [[ $Ans == "y" || $Ans == "Y" || $Ans == "yes" || $Ans == "Yes" || $Ans == "" ]]
	then
    	  echo 
	else
		echo -e "\nYou chose not to continue..."
	  	echo -e "\n\033[36mYou have enabled the \033[0m$CURSOR \033[36mcursor theme with size unchanged of \033[0m$CURRENTSIZE\033[36m \nYou need to log out to complete the change:\033[0m";
		echo
	        read -n 1 -p "Press any key to exit this script..."
exit
fi

## Edits dconf to reflect chosen size
gsettings set org.gnome.desktop.interface cursor-size $SIZE

## Creates a ~/.Xresources file or edits existing to reflect chosen size
if grep "Xcursor.size:" ~/.Xresources > /dev/null; then
	#echo "Xcursor.size line exists"
	sed -i "/Xcursor.size/c\Xcursor.size:${SIZE}" ~/.Xresources
else
	#echo "Xcursor.size line does not exist"
	echo "Xcursor.size:${SIZE}" >> ~/.Xresources
fi


echo -e "\n\033[36mYou have enabled the \033[0m$CURSOR \033[36mcursor theme of size \033[0m$SIZE\n\033[36mYou need to log out to complete the change:\033[0m";

echo
read -n 1 -p "Press any key to exit this script..." 
```

You can run by dragging and dropping the script into a terminal.
The script has a component to change size but only works with cursor themes that have multiple sizes
so don't worry about that section.
Look for any errors when the script is run.

---

### Post by hasanaa on 2014-11-01
```
Your current cursor theme is 'simpleandsoft' 
     1    simpleandsoft
wc: /home/glen/.cursorlist.txt: No such file or directory
Enter your new theme selection number:

```

i chosed 1 and nothing happens.

---

### Post by CantankRus on 2014-11-01
Last try.

run each line one after the other in the same terminal....
```
CURSOR="simpleandsoft"
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/"$CURSOR"/cursor.theme 20
gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR"
sudo update-alternatives --set x-cursor-theme /usr/share/icons/"$CURSOR"/cursor.theme
```

---

### Post by hasanaa on 2014-11-01
i did. restarted the system but dmz-black still on my desktop. tnx anyway

---

### Post by CantankRus on 2014-11-01
> **hasanaa said:**
> i did. restarted the system but dmz-black still on my desktop. tnx anyway

This all should work.
Last bit of info.
In **/usr/share/icons/default** you should have an **index.theme** file which is a link to **/etc/alternatives/x-cursor-theme**
When simpleandsoft is set as the cursor it should look as in pic.

---

### Post by oldefoxx on 2015-05-17
Using some of the techniques discussed here (as well as others touted elsewhere, and some I attedmpted with little quidance), I have this displayed in sudo mode on my terminal screen:

```
# update-alternatives --display x-cursor-theme
x-cursor-theme - manual mode
  link currently points to /usr/share/icons/FlatbedCursors.White.Large/cursor.theme
/etc/X11/cursors/core.theme - priority 30
/etc/X11/cursors/handhelds.theme - priority 20
/etc/X11/cursors/redglass.theme - priority 20
/etc/X11/cursors/whiteglass.theme - priority 20
/usr/share/icons/ComixCursors-White/index.theme - priority 20
/usr/share/icons/DMZ-Black/cursor.theme - priority 30
/usr/share/icons/DMZ-White/cursor.theme - priority 100
/usr/share/icons/FlatbedCursors.White.Large/cursor.theme - priority 20
/usr/share/icons/FlatbedCursors.White.Large/index.theme - priority 20
Current 'best' version is '/usr/share/icons/DMZ-White/cursor.theme'.

```

Actually I want a bigger, more pronounced cursor than DMZ-White provides.  Biggest problem with my cursor theme efforts has been that they are not global in their use under Metacity (flashback to the classical gnome interface).  Nothing cursor-wize seems global in nature with Ubuntu 14.04.

But immediate issue for me is how do I get rid of some of the themes being listed here?  Such as "**/usr/share/icons/FlatbedCursors.White.Large/index.theme - priority 20**"?  I used --install for this in an early effort to get things right, and now I want to blot it out.  And where soes that "**Current "best" version**" derive from?  And what influence does it have on cursor selection at verious points and by various applications?

I found a number of cursor theme choices at GNOME-look.org, and on some of the pages there, you can scroll to the bottom of the page and download some of the artwork to replace or add new themes to your system.  But beyond that, I've yet to find a reliable way to make any changes in cursor size or theme either global in nature or specific to a certain context.

Most of my thoughts and experience thus far have been summed up here in this post.  But somehow, have not gone far enough.  More help would be greatly appreciated.  So **_HELP_**!  Please?  And Thank you.

---

### Post by CantankRus on 2015-05-17
Probably the easiest way to remove themes added to alternatives is to
install and use galternatives.
```
sudo apt-get install galternatives
```

After installing you will need to fix a bug in the 14.04 version of galternatives
by running this create link command...
```
sudo ln -s /usr/bin/update-alternatives /usr/sbin/
```

Then open galternatives to x-cursor-theme and select and delete the themes you wish.
Only deletes from alternatives. The themes will still remain in **/usr/share/icons** or wherever you placed them.

You can download larger cursors [**_[COLOR="#B22222"]HERE[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2048046&p=12735911#post12735911")

And to install and use here is a [**_[COLOR="#B22222"]guide for Ubuntu Unity[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2221942&p=13018154#post13018154")
Don't know if this works in elementary.

---

### Post by oldefoxx on 2015-05-17
I found **contrastLarge** on gnome-look.org rather to my liking (go to** [http://gnome-look.org/content/show.php/ContrastLarge?content=20568](http://gnome-look.org/content/show.php/ContrastLarge?content=20568)**, and after downloading it to my Downloads folder and extracting it with the archive manager to my Desktop, I followed the instructions in the readme file found in the new contrastLarge folder.  It's pretty simple, and has actually worked, for the most part.  Firefox wants to keep using the older FlatbedCursors.White.Large that I had gotten from the same site, so next trick is to try and figure out how to get the new cousors to go global.  Any ideas on what to try next?

---

### Post by CantankRus on 2015-05-17
Can't test in Elementary but for Unity I would do this.

I have downloaded the contrastlarge cursor theme and extracted to my Desktop folder.

The theme doesn't have a cursor.theme file.
Create one in your text editor and paste in and save the following...
```
[Icon Theme]
Inherits=contrastlarge
```

Open a terminal and change directory to your Desktop...
```
cd ~/Desktop
```

Move the theme to /usr/share/icons...
```
sudo mv contrastlarge /usr/share/icons
```

Install the theme to alternatives, select the theme in alternatives and dconf.
Run each line one at a time.
```
CURSOR=contrastlarge
sudo update-alternatives --install /usr/share/icons/default/index.theme x-cursor-theme /usr/share/icons/"$CURSOR"/cursor.theme 20
gsettings set org.gnome.desktop.interface cursor-theme "$CURSOR" && sudo update-alternatives --set x-cursor-theme /usr/share/icons/"$CURSOR"/cursor.theme
```

Log out.

PS: The DMZ-White-Medium theme I linked to earlier looks a lot better than the contrastlarge theme.

---

