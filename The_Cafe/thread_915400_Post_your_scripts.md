---
title: "Post your scripts?"
date: 2008-09-09
forum: The Cafe
---

### Post by phrostbyte on 2008-09-09
I am trying to build a script repository over at [http://www.launchpad.net/scripting]("http://www.launchpad.net/scripting"). Only one problem - I don't have many scripts of my own!

Have any useful scripts you made (in sh, bash, python, perl, ruby, etc.)? Share them with the world! 

Please reply to this thread with:
*  The script you wrote. 
*  What of the following licences you want it under: GPLv3, BSD/BSD-like, or public domain.
*  Your name that you want to be credited as in the script.

Or alternatively you can upload a branch to the project's BZR tree, if you have a lot of scripts and know how to use BZR. No special permission/access is required.

Thank you!

---

### Post by niccholaspage on 2008-09-09
Awesome SH script to run Firefox On A USB Device.Code:
```

#!/bin/sh
check=`ps -e | grep "firefox"`
if check=0
then
zenity --info --text "Please Close any Firefox Proccesses"
else
./AppLinux/run-mozilla.sh ./AppLinux/firefox-bin -profile ./Data/profile
fi

```Instructions on how to use this script is at my non so popular blog:sanassar.blogspot.com

---

### Post by phrostbyte on 2008-09-09
> **niccholaspage said:**
> Awesome SH script to run Firefox On A USB Device.Code:
```

#!/bin/sh
check=`ps -e | grep "firefox"`
if check=0
then
zenity --info --text "Please Close any Firefox Proccesses"
else
./AppLinux/run-mozilla.sh ./AppLinux/firefox-bin -profile ./Data/profile
fi

```Instructions on how to use this script is at my non so popular blog:sanassar.blogspot.com

Is that the entire script or run-mozilla.sh is another part? :)

---

### Post by bodhi.zazen on 2008-09-09
[http://bodhizazen.net/adblock/adblock-0.98.sh.txt](http://bodhizazen.net/adblock/adblock-0.98.sh.txt)

direct link : [http://bodhizazen.net/adblock/adblock-0.98.sh](http://bodhizazen.net/adblock/adblock-0.98.sh)

Additional information (README) : [http://bodhizazen.net/adblock/](http://bodhizazen.net/adblock/)

As stated in the readme , GPL V3 , please credit to, well

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

### Post by niccholaspage on 2008-09-09
run-mozilla.sh is in the firefox.tar.bz2 package.Also,Remove the if and check things.This is messed up right now..

---

### Post by -grubby on 2008-09-09
Here's a **very small** script I just wrote, that only works in Fluxbox (Or any other envirornment that can use fbsetbg). It randomly sets wallpapers. Configure a directory on the top line. It depends on fbsetbg (which oddly doesn't seem to be in the Ubuntu repositories anymore :|)

Anyways, 

[php]
# The dir the script takes wallpapers from
directory = "/home"

def main() :
    import random, os

    wallpapers = os.listdir(directory)
    # Randomly select a wallpaper from the list of wallpapers in the wallpaper directory
    os.popen("fbsetbg -f %s" % (random.choice(wallpapers)))

if __name__ == "__main__" : # Prevent from running script if imported
    main()
[/php]

EDIT: Oh, and, it's in Python. Run it whenever you want to randomly change backgrounds, or make it a cronjob

---

### Post by OutOfReach on 2008-09-09
I don't know if you would consider this 'useful' (probably not) but this script copies files with a certain file extension (in the current directory) to a specified directory. I made it to copy some of my .py files that were mixed in with some other file extensions, to my usb stick.

MultiCopy.py:
[PHP]import sys
import os
import shutil

#This small script moves files in the current directory with the specified file extension
#to a the specified directory.

if len(sys.argv[1:]) == 0:
	print "You did not specify any arguments."
	print "Proper Syntax: ./MultiCopy.py [FILE EXTENSION] [MOVING DIRECTORY]"
	exit()

if sys.argv[1].startswith("."):
	file_extension = sys.argv[1]
else:
	file_extension = ".%s" % sys.argv[1]
copy_dir = sys.argv[2]

for x in os.listdir(os.getcwd()):
	if x.endswith(file_extension):
		shutil.copy2(x, copy_dir)
		
print "Finished."
[/PHP]

---

### Post by LaRoza on 2008-09-09
A script for making a back up restore point of all packages installed, and can restore them (for a fresh install, borked system, etc). **Do not use with sysres. They were made a while ago, and do not work together**
```

#!/bin/bash

#sysres: Linux system restore program.
#Copyright (C) 2008  LaRoza

#This program is free software: you can redistribute it and/or modify
#it under the terms of the GNU General Public License as published by
#the Free Software Foundation, either version 3 of the License, or
#(at your option) any later version.

#This program is distributed in the hope that it will be useful,
#but WITHOUT ANY WARRANTY; without even the implied warranty of
#MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#GNU General Public License for more details.

#You should have received a copy of the GNU General Public License
#along with this program.  If not, see <http://www.gnu.org/licenses/>.

nochange()
{
    zenity --info --text "Package Backup and Restore Halted -- No Changes Made";
    exit 0;
}

restore()
{
    if [ $UID -eq 0 ]
        then
        name=$(zenity --file-selection --text "Open file:" --filename ~/.system_restore/);

        zenity --question --text "Install all packages?";
        
        if [ $? -eq 0 ] 
        then

            if [ -f $name ]
            then
                zenity --info --text "File exists and ready";
                gksudo dpkg --set-selections < $name; dselect;
            else
                zenity --info --text "Not a file";
                nochange;
            fi

        else
            nochange;
        fi
    else
        zenity --info --text "You are not root";
        exit 0
    fi

    return;  
}
backup()
{
    saveas=$(zenity --entry --text "Save as:");
     
    if [ -e ~/.sysres/$saveas ]
    then  
        if [ -d ~/.sysres/$saveas ]
        then
            zenity --info --text "That is a directory";
            nochange;
        fi

        zenity --question --text "File exists, overwrite?";

        if [ $? -eq 0 ] 
        then
            dpkg --get-selections > ~/.sysres/$saveas;
        else
            exit;
        fi
        
    else
        dpkg --get-selections > ~/.sysres/$saveas;
    fi

    return;
}


main()
{
    ans=$(zenity  --list  --text "Package Backup and Restore" --radiolist  --column "Pick" --column "Option" TRUE "Backup" FALSE "Restore");

    if [ $? -eq 1 ]
    then
        nochange;
    else
        if [ $ans == "Backup" ] 
        then
            backup;
        elif [ $ans == "Restore" ]
        then
            restore;
        else
            nochange;
        fi
    fi
        
}

main;

```

---

### Post by smartboyathome on 2008-09-09
Simple command line video encoder for Insignia Sport. It requires mencoder to be installed. Licensed under GPLv2 or later.

```
#!/bin/sh
# **********************************************
# *           Insignia Video Encoder           *
# * Encodes your video for your Insignia sport *
# *             By smartboyathome              *
# **********************************************

echo "Type the path to your video that you want to encode and press [ENTER]: "
read pathdecoded

echo "Type where you want the encoded video to be put (including the video's file name) and press [ENTER]: "
read pathencoded

echo "Encoding, please wait..."
mencoder $pathdecoded -ovc lavc -oac mp3lame -lameopts cbr:br=128 -ffourcc XVID -lavcopts vcodec=mpeg4:vbitrate=256 -vf scale=220:176,crop=220:176 -ofps 15 -o $pathencoded >/dev/null 2>/dev/null

# WMV to AVI
# mencoder $pathdecoded -ofps 23.976 -ovc lavc -oac copy -o outfile.avi

echo "Done!"
```

---

### Post by mitch_feaster on 2008-09-09
Here's a nasty little one just to facilitate connecting to a wireless network from the terminal.  (Note: there is currently no support for encryption...Sad, I know but that's all I needed it for.)

Licensed under the 'feasters only general public license'.

```

#!/bin/bash

# this script was written by Mitchel Humpherys
# to facilitate the connection of the rotaryngurder
# to the chemical reactor in Chris's pants
# licensed under the feaster's only general public license

# check for root priveledges:
if [[ $EUID -ne 0 ]]; then
	echo -e "This script must be run as root.\n Try 'sudo connecter'" 1>&2
	exit 1
fi
 
echo -e "You can select from the following networks:\n"
iwlist scan 2>/dev/null | grep -i essid
echo -e "Which network would you like to connect to? "
read -e NETWORK
echo -e "Okay let's do it!\n"

ifconfig eth0 down
ifconfig wlan0 down
dhclient -r wlan0
iwconfig wlan0 essid $NETWORK
iwconfig wlan0 mode Managed
ifconfig wlan0 up
dhclient wlan0

exit 0


```

---

### Post by phrostbyte on 2008-09-10
I added LaRoza and bodhi.zazen's scripts to the repository. I could not add anyone else because you either didn't state what license you wanted it under, or you choose a license not compatible with the stated license options. Please fix if you can. :)

---

### Post by smartboyathome on 2008-09-10
> **phrostbyte said:**
> I added LaRoza and bodhi.zazen's scripts to the repository. I could not add anyone else because you either didn't state what license you wanted it under, or you choose a license not compatible with the stated license options. Please fix if you can. :)

GPLv2 is compatible with GPLv3. The Linux kernel itself is still under GPLv2, and yet you run some programs licensed under GPLv3. So you can add mine. :)

---

### Post by phrostbyte on 2008-09-10
> **smartboyathome said:**
> GPLv2 is compatible with GPLv3. The Linux kernel itself is still under GPLv2, and yet you run some programs licensed under GPLv3. So you can add mine. :)

I'm trying to avoid too many different copyleft licenses, so I settled on one major copyleft license as to avoid legal confusion. But I can add it if you add the language "GPLv2 or higher". Thanks!

---

### Post by smartboyathome on 2008-09-10
Fine, I will put it at GPLv2 or higher (I thought the higher was implied, since it says that GPLv2 programs can be forked and licensed under GPLv3).

---

### Post by phrostbyte on 2008-09-10
> **smartboyathome said:**
> Fine, I will put it at GPLv2 or higher (I thought the higher was implied, since it says that GPLv2 programs can be forked and licensed under GPLv3).

I've added your script to the BZR tree.

People please keep it coming, we are up to 5 now! I know we can do 10 =).

---

