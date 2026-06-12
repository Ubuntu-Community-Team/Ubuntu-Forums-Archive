---
title: "Bored: any lxde tips?"
date: 2010-02-25
forum: The Cafe
---

### Post by kerry_s on 2010-02-25
any lxde users want to share some of your tips, tricks, tweaks?

my linux is getting rusty so i'm playing with the lxde desktop, but i just have no ideas what i want to do with it. so far i just been simplifing it cause i have to keep it simple, i'm shareing this computer with my niece, she has downs syndrome.

specs:
vaio pcg-f430 laptop
450 mhz
256 mb ram

i've played with the looks.(see pic)

i created a "root open" in ~/.local/share/applications/root.desktop so i can just right click on the folder/file and open it as root instead of using the "tool" button.

```
[Desktop Entry]
Encoding=UTF-8
Name=Root Open
Exec=gksudo gnome-open %U
Icon=gksu.png

```

added mvp's host block list to kill ad's

hmm... nothing else comes to mind :(

---

### Post by urukrama on 2010-02-25
This is fun for a while: [http://urukrama.wordpress.com/2008/05/23/expose-type-behaviour-in-openbox/](http://urukrama.wordpress.com/2008/05/23/expose-type-behaviour-in-openbox/)

---

### Post by kerry_s on 2010-02-25
> **urukrama said:**
> This is fun for a while: [http://urukrama.wordpress.com/2008/05/23/expose-type-behaviour-in-openbox/](http://urukrama.wordpress.com/2008/05/23/expose-type-behaviour-in-openbox/)

interesting, thanks! i try not run to many app's cause of my low specs, so not really worth bothering with for me.

---

### Post by mkvnmtr on 2010-02-25
I found that when I instlled LXDE on a minimal install it pulled in gdm. This uses a lot of resources so I uninstalled it and just log in from the command line and type startx.If you want a log in manager that uses less resources lyou can try slim. It seems that LXDE in a Ubuntu install pulles in many packages that are not needed so I have quit using it and gone back to xfce4.The way I set it up on a light install it is not much different than LXDE and without the extra dependencies is just as light on ram and cpu usage.

---

### Post by dzon65 on 2010-03-20
Give slitaz a shot Kerry.Run it from ram,256 mb will feel like 1Gb.

---

### Post by juancarlospaco on 2010-03-20
add to startup apps:

xdesktopwaves &

---

### Post by kerry_s on 2010-03-20
i forgot all about this thread. :lolflag:
i'll put the script here for lxshortcut.
i'll work on the messy echo command, so it's doesn't list "Categories" several time when editing, as soon as i figure out sed i'll up date the script.

pics here: [http://ubuntuforums.org/showthread.php?p=8995340#post8995340](http://ubuntuforums.org/showthread.php?p=8995340#post8995340)

```

#!/bin/bash

# this is a script to add some gui features to lxshortcut for a more user friendly experience
# created on lubuntu 10.04 3/19/2010
# it's a script to fill a need, you may do with it as you please
###

## this part is the choices to choose from ##

chose=`zenity --list --title="Lxshortcut-gui" --column="" "Make Launcher" "Edit Launcher" "Delete Launcher"`

## this part makes the launcher ##

if [ "$chose" = "Make Launcher" ]; then

	name=`zenity --entry --text="Enter a Name (example: xterm)
	this will not be the name shown, it's only for the *.desktop file"`

	if [ "$name" ]; then
	 lxshortcut -o $HOME/.local/share/applications/$name.desktop
	 select=`zenity --list --text="Choose the Menu Section" --column="" Utility Graphics 	Network Office AudioVideo System Settings Other`
	 echo "Categories=$select;" >> $HOME/.local/share/applications/$name.desktop
	else
	 exit 0
	fi
fi

## this part is to edit the launcher ##

if [ "$chose" = "Edit Launcher" ]; then

	scan=`ls $HOME/.local/share/applications | grep .desktop`
	selected=`zenity --list --column="" $scan`
	if [ $selected ]; then
	 lxshortcut -i $selected
	 select=`zenity --list --text="Choose the Menu Section" --column="" Utility Graphics 	Network Office AudioVideo System Settings Other`
	 echo "Categories=$select;" >> $HOME/.local/share/applications/$selected
	else
	 exit0
	fi
fi

## this part is to delete the launcher ##

if [ "$chose" = "Delete Launcher" ]; then

	scan=`ls $HOME/.local/share/applications | grep .desktop`
	selected=`zenity --list --column="" $scan`
	if [ $selected ]; then
	 rm $HOME/.local/share/applications/$selected
	 zenity --info --text="Launcher removed"
	else
	 exit 0
	fi
fi
exit 0


```

---

### Post by kerry_s on 2010-03-20
> **juancarlospaco said:**
> add to startup apps:

xdesktopwaves &

i use maximus & nodeco in openbox, so all my apps are full screen, since i don't see my desktop most of the time it would be a waste.

but thanks for the tip!

---

### Post by kerry_s on 2010-03-20
alright here's the redone lxshortcut gui script.
i added some height for less scrolling, hope it's not a problem for netbook users. let me know if you find something else you don't like, better still if you improve the script please share, i know my skills are horrid. 

```

#!/bin/bash

# this is a script to add some gui features to lxshortcut for a more user friendly experience
# created on lubuntu 10.04 3/19/2010
# it's a script to fill a need, you may do with it as you please
###

## this part is the choices to choose from ##

chose=`zenity --list --title="Lxshortcut-gui" --column="" "Make Launcher" "Edit Launcher" "Delete Launcher"`

## this part makes the launcher ##

if [ "$chose" = "Make Launcher" ]; then

	name=`zenity --entry --text="Enter a Name (example: xterm)
	this will not be the name shown, it's only for the *.desktop file"`

	if [ "$name" ]; then
	 lxshortcut -o $HOME/.local/share/applications/$name.desktop
	 select=`zenity --list --height="400" --text="Choose the Menu Section" --column="" Utility Graphics Network Office AudioVideo System Settings Other`
	 echo "Categories=$select;" >> $HOME/.local/share/applications/$name.desktop
	else
	 exit 0
	fi
fi

## this part is to edit the launcher ##

if [ "$chose" = "Edit Launcher" ]; then

	scan=`ls $HOME/.local/share/applications | grep .desktop`
	selected=`zenity --list --height="400" --column="" $scan`
	if [ $selected ]; then
	 lxshortcut -i $selected
	 sed -e '/;$/d' -i $HOME/.local/share/applications/$selected
	 select=`zenity --list --height="400" --text="Choose the Menu Section" --column="" Utility Graphics Network Office AudioVideo System Settings Other`
	 echo "Categories=$select;" >> $HOME/.local/share/applications/$selected
	else
	 exit0
	fi
fi

## this part is to delete the launcher ##

if [ "$chose" = "Delete Launcher" ]; then

	scan=`ls $HOME/.local/share/applications | grep .desktop`
	selected=`zenity --list --height="400" --column="" $scan`
	if [ $selected ]; then
	 rm $HOME/.local/share/applications/$selected
	 zenity --info --text="Launcher removed"
	else
	 exit 0
	fi
fi
exit 0


```

here's a upload if you don't want to copy & paste.

---

### Post by kerry_s on 2010-03-21
for those that would rather use the trash system change:

```
	 rm $HOME/.local/share/applications/$selected

```
to
```
	 gvfs-trash $HOME/.local/share/applications/$selected

```

then if you delete the wrong launcher, you can still save it.

```
## this part is to delete the launcher ##

if [ "$chose" = "Delete Launcher" ]; then

	scan=`ls $HOME/.local/share/applications | grep .desktop`
	selected=`zenity --list --height="400" --column="" $scan`
	if [ $selected ]; then
	 **gvfs-trash** $HOME/.local/share/applications/$selected
	 zenity --info --text="Launcher removed"
	else
	 exit 0
	fi
fi
exit 0
```

---

### Post by kerry_s on 2010-03-22
for those that miss the trash panel applet, you can now get trash notifications in your system tray. just add to your startup an enjoy.

```

#!/bin/bash
#
# created for Lubuntu 10.04 on 3/21/2010
# by falconindy & kerry_s @ http://ubuntuforums.org/showthread.php?p=9006632#post9006632
# this was made to serve a need, do with it as you please.
#
# make sure you have gvfs-bin installed.
###

## this is the path to the trash icon, change to match your theme use "locate user-trash-full" in terminal.
icon=/usr/share/icons/gnome/scalable/status/user-trash-full.svg

## this is the file manager used when clicked.
filemanager=/usr/bin/pcmanfm2

## don't need to touch this.
dir=$HOME/.local/share/Trash/files

while true; do
  [[ $(gvfs-info trash:/// | grep 'trash::item-count: 0') ]] || {
    zenity --notification --window-icon="$icon" --text=" $(gvfs-ls trash:///) ";
    $filemanager $dir; sleep 90;
  }
  sleep 10
done


```

---

### Post by kerry_s on 2010-03-24
a very simple "add to startup" script.

```

#!/bin/bash

start=`zenity --entry --text="Add to startup" `
echo "@$start" >> $HOME/.config/lxsession/Lubuntu/autostart
sed -e '/\@$/d' -i $HOME/.config/lxsession/Lubuntu/autostart


```

---

### Post by kerry_s on 2010-03-24
i decided i wanted to be able to edit the file if i wanted.

```

#!/bin/bash

choose=`zenity --list --column="" "Add to startup" "Edit startup file" `

if [ "$choose" == "Add to startup" ]; then
	start=`zenity --entry --text="Add to startup" `
	echo "@$start" >> $HOME/.config/lxsession/Lubuntu/autostart
	sed -e '/\@$/d' -i $HOME/.config/lxsession/Lubuntu/autostart
fi

if [ "$choose" == "Edit startup file" ]; then
	gnome-open $HOME/.config/lxsession/Lubuntu/autostart
fi


```

---

### Post by kerry_s on 2010-03-24
lubuntu uses scrot for the print key screenshots, well i use a small roll up keyboard that doesn't have a print key, i was using xfce4-screenshooter which is great, but i figured why not make something for scrot, give it some gui love. ;)

```

#!/bin/bash

choose=`zenity --list --column="" "Whole desktop" "Delay screenshot" "Select area" `

if [ "$choose" == "Whole desktop" ]; then
	scrot -d 1 %T.png -e 'mv $f ~/Desktop'
fi

if [ "$choose" == "Delay screenshot" ]; then
	num=`zenity --entry --text="Delay Time" `
	scrot -d $num %T.png -e 'mv $f ~/Desktop'
fi

if [ "$choose" == "Select area" ]; then
	scrot -s %T.png -e 'mv $f ~/Desktop'
fi
exit 0


```

---

### Post by kerry_s on 2010-04-13
just saving my scripts off the computer, all my flash drives are being borrowed.

leafpad override, checks if file owner is root, if so open as root.
```

#!/bin/bash

test=`stat -c %U "$@"`
if [ "$test" == "root" ]; then
	gksu /usr/bin/leafpad "$@"
else
	/usr/bin/leafpad "$@"
fi
exit 0

```

gui for lxshortcut, makes it more menu friendly.
```

#!/bin/bash

chose=`zenity --list --height="250" --title="Lxshortcut-gui" --column="" "Make Launcher" "Edit Launcher" "Delete Launcher"`

if [ "$chose" == "Make Launcher" ]; then

	name=`zenity --entry --text="Enter a Name (example: xterm)
	this will not be the name shown, it's only for the *.desktop file"`

	if [ "$name" ]; then
	 lxshortcut -o $HOME/.local/share/applications/$name.desktop
	 select=`zenity --list --height="400" --text="Choose the Menu Section" --column="" Utility Graphics Network Office AudioVideo System Settings Other`
	 echo "Categories=$select;" >> $HOME/.local/share/applications/$name.desktop
	else
	 exit 0
	fi

elif [ "$chose" == "Edit Launcher" ]; then

	scan=`ls $HOME/.local/share/applications | grep .desktop`
	selected=`zenity --list --height="400" --column="" $scan`
	if [ $selected ]; then
	 lxshortcut -i $selected
	 sed -e '/;$/d' -i $HOME/.local/share/applications/$selected
	 select=`zenity --list --height="400" --text="Choose the Menu Section" --column="" Utility Graphics Network Office AudioVideo System Settings Other Hide`
	 
	if [ "$select" == "Hide" ]; then
	 echo "NoDisplay=true" >> $HOME/.local/share/applications/$selected
	exit 0
	fi
	
	sed -e '/NoDisplay=true$/d' -i $HOME/.local/share/applications/$selected
	echo "Categories=$select;" >> $HOME/.local/share/applications/$selected
fi

elif [ "$chose" == "Delete Launcher" ]; then

	scan=`ls $HOME/.local/share/applications | grep .desktop`
	selected=`zenity --list --height="400" --column="" $scan`
	if [ $selected ]; then
	 rm $HOME/.local/share/applications/$selected
	 zenity --info --text="Launcher removed"
	else
	 exit 0
	fi
fi

exit 0

```

gui for scrot to take screen shots.
```

#!/bin/bash

sel=`zenity --title="Screenshot Options" --list --column="" "Whole desktop" "Delay screenshot" "Select area"`

if [ "$sel" == "Whole desktop" ]; then
	scrot -d 1 %T.png -e 'mv $f ~/Desktop'; notify-send "Screenshot done"
elif [ "$sel" == "Delay screenshot" ]; then
	num=`zenity --entry --text="Delay Time"`
	scrot -d $num %T.png -e 'mv $f ~/Desktop'; notify-send "Screenshot done"
elif [ "$sel" == "Select area" ]; then
	scrot -s %T.png -e 'mv $f ~/Desktop'; notify-send "Screenshot done"
fi
exit 0

```

add & edit the startup file.
```

#!/bin/bash

zenity --question --text="Add or Edit autostart" --cancel-label="Edit startup file"  --ok-label="Add startup program"
ans="$?"

if [ "$ans" == "0" ]; then
	start=`zenity --entry --text="Add to startup" `
	echo "@$start" >> $HOME/.config/lxsession/Lubuntu/autostart
	sed -e '/\@$/d' -i $HOME/.config/lxsession/Lubuntu/autostart
elif [ "$ans" == "1" ]; then
	leafpad $HOME/.config/lxsession/Lubuntu/autostart
fi
exit 0

```

---

### Post by kerry_s on 2010-04-24
check gmail:

```

#!/bin/bash

while true; do 

gmail_login="**login-name**"  
gmail_password="**password**" 
icon="/usr/share/icons/gnome/scalable/actions/mail-mark-important.svg"

check="$(wget --secure-protocol=TLSv1 --timeout=3 -t 1 -q -O - \
https://${gmail_login}:${gmail_password}@mail.google.com/mail/feed/atom \
--no-check-certificate | grep 'fullcount' \
| sed -e 's/.*<fullcount>//;s/<\/fullcount>.*//' 2>/dev/null)"

if [ "$check" == "0" ]; then
  sleep 300
 else
  zenity --info --text="You Have Mail"
  zenity --notification --text="$check Unread" --window-icon="$icon"
  gnome-open https://mail.google.com/
  sleep 300
fi

done


```

---

### Post by guy-rouillier on 2010-06-06
> **mkvnmtr said:**
> I found that when I instlled LXDE on a minimal install it pulled in gdm. This uses a lot of resources so I uninstalled it and just log in from the command line and type startx.

I'm new to LXDE.  I got it running fine on 10.4, but I'd like to boot up to a simple login prompt and run startx when desired (this is primarily a file server.)  The default LXDE install starts up lxdm.  Is the correct way to tell it not to start a DM to simply uninstall lxdm?  Or am I supposed to modify some plymouth config somewhere to tell it not to start the dm?

Thanks.

---

### Post by kerry_s on 2010-06-06
edit /etc/default/grub
add "1" to the line

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **1**"
```

run "sudo update-grub"

---

### Post by guy-rouillier on 2010-06-06
> **kerry_s said:**
> edit /etc/default/grub
add "1" to the line

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **1**"
```run "sudo update-grub"

Didn't work for me.  That line in my file has the following:

```

GRUB_CMDLINE_LINUX_DEFAULT="quiet"

```When I changed it to "quiet splash 1", upon reboot Ubuntu popped up a recovery menu.  I tried "quiet 1" and the same thing happened.  And yes, I did run "update-grub" after making those changes.

Other ideas?

---

### Post by guy-rouillier on 2010-06-16
I found a solution that works for me here:

[http://ubuntuforums.org/showthread.php?p=9470029#post9470029](http://ubuntuforums.org/showthread.php?p=9470029#post9470029)

This info should go into a wiki, as the question seems to come up from time to time.

---

### Post by kerry_s on 2010-06-16
> **guy-rouillier said:**
> I found a solution that works for me here:

[http://ubuntuforums.org/showthread.php?p=9470029#post9470029](http://ubuntuforums.org/showthread.php?p=9470029#post9470029)

This info should go into a wiki, as the question seems to come up from time to time.

so it's now "text" instead of "1", thanks for the heads up.

---

### Post by Jared Norris on 2010-10-09
> **kerry_s said:**
> check gmail:

```

#!/bin/bash

while true; do 

gmail_login="**login-name**"  
gmail_password="**password**" 
icon="/usr/share/icons/gnome/scalable/actions/mail-mark-important.svg"

check="$(wget --secure-protocol=TLSv1 --timeout=3 -t 1 -q -O - \
https://${gmail_login}:${gmail_password}@mail.google.com/mail/feed/atom \
--no-check-certificate | grep 'fullcount' \
| sed -e 's/.*<fullcount>//;s/<\/fullcount>.*//' 2>/dev/null)"

if [ "$check" == "0" ]; then
  sleep 300
 else
  zenity --info --text="You Have Mail"
  zenity --notification --text="$check Unread" --window-icon="$icon"
  gnome-open https://mail.google.com/
  sleep 300
fi

done


```

Kerry,

I spent ages looking for anything like this for Lubuntu. I kept getting crashes with "mail-notification" (what I use under gnome) whenever I tried to add a gmail account with various Glib and GTK errors. 

This is perfect and is greatly appreciated.

---

### Post by BrokenTusk on 2010-12-24
> **kerry_s said:**
> any lxde users want to share some of your tips, tricks, tweaks?

i created a "root open" in ~/.local/share/applications/root.desktop so i can just right click on the folder/file and open it as root instead of using the "tool" button.

```
[Desktop Entry]
Encoding=UTF-8
Name=Root Open
Exec=gksudo gnome-open %U
Icon=gksu.png

```

Love this thread cause i recently fell for LXDE. here's how I made my ROOT open script/servicemenu entry work:
```

[Desktop Entry]
Type=Service
ServiceTypes=KonqPopupMenu/Plugin
MimeType=application/octet-stream;
Actions="Open as ROOT";

[Desktop Action "Open as ROOT"]
Name=Open as ROOT
Icon=bball
Exec=gnomesu gnome-open %F

```
This .desktop file goes into: "/usr/share/kde4/services/ServiceMenus" then it shows up in the right-click>Actions menu.
Again thanks for your tips and I'll come back to add more of my own.

---

### Post by Pocio on 2011-01-15
> **kerry_s said:**
> for those that miss the trash panel applet, you can now get trash notifications in your system tray. just add to your startup an enjoy.

```

#!/bin/bash
#
# created for Lubuntu 10.04 on 3/21/2010
# by falconindy & kerry_s @ http://ubuntuforums.org/showthread.php?p=9006632#post9006632
# this was made to serve a need, do with it as you please.
#
# make sure you have gvfs-bin installed.
###

## this is the path to the trash icon, change to match your theme use "locate user-trash-full" in terminal.
icon=/usr/share/icons/gnome/scalable/status/user-trash-full.svg

## this is the file manager used when clicked.
filemanager=/usr/bin/pcmanfm2

## don't need to touch this.
dir=$HOME/.local/share/Trash/files

while true; do
  [[ $(gvfs-info trash:/// | grep 'trash::item-count: 0') ]] || {
    zenity --notification --window-icon="$icon" --text=" $(gvfs-ls trash:///) ";
    $filemanager $dir; sleep 90;
  }
  sleep 10
done


```

Thanks for all these wonderful script!
I love them!
Unfortunately, this one does not work for me...I see the icon in the tray, but when I click on it pcmanfm does not open the trash folder...

I solved by changing in this way
```

## this is the file manager used when clicked.
filemanager=/usr/bin/pcmanfm

## don't need to touch this.
dir=trash:///

```

Thanks again!

---

### Post by Spice Weasel on 2011-01-15
> **juancarlospaco said:**
> add to startup apps:

xdesktopwaves &

Thank you. :D

---

