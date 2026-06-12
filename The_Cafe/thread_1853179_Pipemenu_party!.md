---
title: "Pipemenu party!"
date: 2011-10-01
forum: The Cafe
---

### Post by jazzerit on 2011-10-01
[SIZE="4"]Come one, come all to this; my communal pipemenu dump![/SIZE] This is where we dump pipemenus for openbox! So, my foxes, come and eat of the proverbial rubbish dump here, and regurgitate old pipemenus for openbox back onto it. I'll start.

[SIZE="2"]Script one: The run menu[/SIZE]
This script allows you to start a run dialog, except in it's menu it has the last five run commands. It relies on zenity and the GNU coreutils, and needs the dialog pipemenu to be saved in ~/.config/openbox as openbox-rundialog-dialog.sh, and made executable.
pipemenu:
```
#!/bin/bash
echo "<openbox_pipe_menu>"
echo "<item label=\"Run...\"><action name=\"Execute\"><execute>~/.config/openbox/openbox-rundialog-dialog.sh</execute></action></item>"
echo "<separator/>"
cat ~/.config/openbox/rundialog_history | tail -n 5 | while read line; do
echo "<item label=\"$line\"><action name=\"Execute\"><execute>$line</execute></action></item>"
done
echo "</openbox_pipe_menu>"

```
Dialog:```
#!/bin/bash
command=$(zenity --entry --text="Enter command:" --title="Run...")
echo $command >> ~/.config/openbox/rundialog_history
exec $command
```
[SIZE="2"]Script two: The exaile remote[/SIZE]
This script allows you to control exaile. It relies on exaile, the gnu coreutils, ps and grep.
Pipemenu:```
#!/bin/bash
echo "<openbox_pipe_menu>"
process=$(ps aux | grep "python /usr/lib/exaile/exaile.py" | grep -v grep)
if [ -z "$process" ]; then
echo "<item label=\"Start Exaile\"><action name=\"Execute\"><execute>exaile</execute></action></item>"
qt='"'
fi
vol="$(exaile --get-volume)"
version="$(exaile --version)"
if [ -n "$process" ]; then
echo "<separator />"
echo "<separator />"
echo "<menu id=\"main\" label=\"Exaile ${version##*v}\">"
echo "<menu id=\"volume\" label=\"volume: ${vol%%.*}%\">"
echo "<item label=\"Increase\"><action name=\"Execute\"><execute>exaile -i 10</execute></action></item>"
echo "<item label=\"Decrease\"><action name=\"Execute\"><execute>exaile -l 10</execute></action></item>"
echo "<item label=\"mute/unmute\"><action name=\"Execute\"><execute>exaile -m</execute></action></item>"
echo "</menu>"
echo "<item label=\"play/pause\"><action name=\"Execute\"><execute>exaile -t</execute></action></item>"
echo "<item label=\"Next track\"><action name=\"Execute\"><execute>exaile -n</execute></action></item>"
echo "<item label=\"Previous track\"><action name=\"Execute\"><execute>exaile -p</execute></action></item>"
echo "<item label=\"Stop\"><action name=\"Execute\"><execute>exaile -s</execute></action></item>"
echo "<item label=\"Stop after current track\"><action name=\"Execute\"><execute>exaile --stop-after-current</execute></action></item>"
echo "</menu>"
echo "<separator />"
echo "<separator label=\"$(exaile --get-title)\"/>"
echo "<separator label=\"by $(exaile --get-artist)\"/>"
echo "<separator />"
echo "<item label=\"Kill exaile\"><action name=\"Execute\"><execute>killall exaile</execute></action></item>"
echo "<separator />"
echo "<separator />"
fi
echo "</openbox_pipe_menu>"
```

[SIZE="2"]Script three: The rss reader[/SIZE]
This pipemenu reads rss feeds, and puts a separator between each feed with the website that the rss feed comes from. It shows the header, and opens each link with xdg-open. It relies on the coreutils and wget. You also need to create a file called openbox-rss-feeds-list in ~/.config/openbox containing the links to your rss feeds.
Pipemenu:
```
#!/bin/bash
rdom () { local IFS=\> ; read -d \< E C ;}
echo "<openbox_pipe_menu>"
echo "<item label=\"edit feeds\"><action name=\"Execute\"><execute>xdg-open ~/.config/openbox/openbox-rss-feeds-list</execute></action></item>"
echo "<menu id=\"rss-main\" label=\"feeds\">"
cat ~/.config/openbox/openbox-rss-feeds-list | while read address; do
nohttp=${address//"http://"/}
nodirs=${nohttp%%/*}
echo "<separator label=\"$nodirs\"/>"
wget --user-agent="Mozilla/5.0 (X11; U; Linux i686; en-US) AppleWebKit/533.4 (KHTML, like Gecko) Chrome/5.0.375.55 Safari/533.4" -q $address -O - | while rdom; do



    if [ "$E" = "title" ]; then
      echo -n "<item label=\"$C\">"
    fi
    if [ "$E" = "link" ]; then
      echo "<action name=\"Execute\"><execute>xdg-open $C</execute></action></item>"
    fi





   done | tail -n +2

done
echo "</menu>"
echo "</openbox_pipe_menu>"
```

[SIZE="2"]Script four: The device menu[/SIZE]
This script shows the partitions of mounted block devices, optical disks, and loop devices. It gives the mountpoint and device file for block devices, and lets you open disk management for them or a filemanager. For optical disks, it shows the type of media and lets you eject or open with a filemanager. For loop devices, it shows device file, mountpoint and name. It lets you open a filemanager either inside the mounted file, or the folder containing the file. In addition, the script also lets you choose whether to show disk manager, eject option or trash option, and lets you set the filemenager, device manager, eject program and trash manager. It's all configured inside the script itself. It relies on GNU coreutils, proc and dev filesystems, grep, udisks, mount and blkid.
Pipemenu:
```
#!/bin/bash



##############################################################################
##############################################################################
##########CONFIGURATION#######################################################
##############################################################################
##############################################################################
filemanager='nautilus --no-desktop '  #points to your favoured file manager. If this isn't working, try removing or deleting a space as applicable on this variable.
diskmanager='palimpsest --show-volume=' #points to your favoured disk manager. If this isn't working, try removing or deleting a space as applicable on this variable.
##############################################################################
showbin='true' #set as either true or false (defaults to true). Sets whether to link to the rubbish bin in the menu or not.
bincommand='nautilus --no-desktop trash://' #the command to use to open the rubbish bin. Not needed if showbin=false.
##############################################################################
showeject='true' #set as either true or false (defaults to true). Sets whether to show an eject option for optical disks.
ejectcommand='eject -T' #points to the command to use for ejecting disks
##############################################################################
showdm='true' #set as either true or false (defaults to true). Sets whether to show a disk management option for block devices.
##############################################################################
##############################################################################
##########END CONFIGURATION###################################################
##############################################################################
##############################################################################




echo "<openbox_pipe_menu>" #start of pipemenu


###############
#block devices#
###############
list=$(ls /sys/block | grep -v ram* | grep -v loop* | grep -v fd* | while read line; do ls /dev | grep $line; done)
devs=$(echo "$list" | while read line; do blkid /dev/$line; done)
echo "$devs" | while read line; do
  device=${line%%:*}
  devline=$(mount | grep $device)
  devlinepass1=${devline##/dev/*on }
  mountpoint=${devlinepass1%% type *}
  devlinepass1=
  devline=
  if [ -n "$mountpoint" ]; then
    echo "<menu id=\"$device\" label=\"$device mounted at $mountpoint\">"
    echo "<item label=\"open in file manager\"><action name=\"Execute\"><execute>$filemanager\"$mountpoint\"</execute></action></item>"
    if [ ! "$showdm" = "false" ]; then
      echo "<item label=\"open in disk utility\"><action name=\"Execute\"><execute>$diskmanager$device</execute></action></item>"
    fi
    echo "</menu>"
  fi
done


###############
#optical disks#
###############
ls /sys/block | grep 'sr\|scd' | while read optdisks; do
  line=$(udisks --show-info /dev/$optdisks | grep "has media:" | column -t | grep -w 1)
  if [ -n "$line" ]; then
    media1=$(udisks --show-info /dev/$optdisks | grep media: | column -t | grep -v rotational | grep -v has | column -t | tr '_' ' ')
    media=${media1##media:}
    echo "<separator/>"
    echo "<menu id=\"device\" label=\"$media\">"
    echo "<item label=\"Open in file manager\"><action name=\"Execute\"><execute>$filemanager\"cdda://sr0/\"</execute></action></item>"
    if [ ! "$showeject" = "false" ]; then
      echo "<item label=\"eject disk\"><action name=\"Execute\"><execute>$ejectcommand</execute></action></item>"
    fi
    echo "</menu>"
  fi
done


##############
#loop devices#
##############
list=$(mount | grep /dev/loop)
if [ -n "$list" ]; then
  echo "<separator/>"
fi
echo "$list" | while read line; do
  device=${line%% on /*}
  label=$(blkid $device | tr ' ' '\n' | while read line; do if [[ "$line" == "LABEL="* ]]; then echo $line; fi; done)
  label2=${label##LABEL=\"}
  label=${label2%%\"}
  label2=
  mountpoint=${line##$device on }
  mountpoint2=${mountpoint%% type *}
  mountpoint="$mountpoint2"
  mountpoint2=
  losetupline=$(losetup -a | grep $device)
  source1=${losetupline##$device*(}
  source2=${source1%%)}
  source=$(dirname "$source2")
  losetupline=
  source1=
  source2=
  if [ -n "$mountpoint" ]; then
    echo "<menu id=\"$label\" label=\"$label($device) mounted at $mountpoint\">"
    echo "<item label=\"Open in file manager\"><action name=\"Execute\"><execute>$filemanager\"$mountpoint\"</execute></action></item>"
    echo "<item label=\"Open source directory in file manager\"><action name=\"Execute\"><execute>$filemanager\"$source\"</execute></action></item>"
    echo "</menu>"
  fi
done


#############
#rubbish bin#
#############
if [ ! "$showbin" = "false" ]; then
  echo "<separator/>"
  echo "<item label=\"Rubbish bin\"><action name=\"Execute\"><execute>$bincommand</execute></action></item>"
fi


echo "</openbox_pipe_menu>" #end of pipemenu

```

---

### Post by jazzerit on 2011-10-01
Also, because I'm nice, I'll post these: These I made for openbox, and should (mostly) work with other WMs and DEs. The logout section for the exit script needs to be edited, it just kills openbox, as does the lock section which uses my own lock thing. It relies on gtkdialog, dbus and hal. I made it because I needed to have a shutdown thing in openbox as well, and unless you're root, or using these franky long dbus messages, you can't do that using GDM but not gnome. The updater relies on apt, zenity, the coreutils, gksudo, sudo and grep. I made it because I couldn't work out how to get the ubuntu update manager to just report updates without root password in openbox. This only needs root password for actually installing things. I put it in my autostart, and if there are no updates, it'll autoclose.

I've tarred it all up, as the exit dialog needs some pictures. The exit script is inside the folder named exit.

---

