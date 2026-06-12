---
title: "HOWTO: XPlanet"
date: 2005-07-16
forum: Tutorials
---

### Post by Psycho275 on 2005-07-16
First of all, [XPlanet](http://xplanet.sourceforge.net)  displays the current daylight conditions in the world, as you desktop background.

[Screenshot](http://www.psycho275.info/images/xplanet_desktop.png)


First of all, install XPlanet:
```
$ sudo apt-get install xplanet
```


Once installed, you have two options:

1) Navigate to the xplanet folder and download some images to use for XPlanet. You will need to replace USERNAME with your user name.

```
$ cd /home/USERNAME/.xplanet/images/
$ wget http://visibleearth.nasa.gov/images/2433/land_shallow_topo_2048.jpg
$ mv land_shallow_topo_2048.jpg earth.jpg
$ wget http://visibleearth.nasa.gov/images/1438/earth_lights_lrg.jpg
$ mv earth_lights_lrg.jpg night.jpg
```

or

2) Install xplanet-images (thanks to mike998 for the info):

```
$ sudo apt-get install xplanet-images
```

Next, we need to stop nautilus from controlling the desktop:
Applications > System Tools > Configuration Editor
In the Configuration Editor, go to apps > nautilus > preferences and untick "show_desktop".

Finally, we need to start XPlanet when we log in:
System > Preferences > Sessions
Click on the "Startup Programs" tab, and click on "Add". Enter "xplanet" (without the quotes) into the "Startup Command" text box, and click OK.

Log out and back in, and you should see an image of earth as your background.

---

### Post by mike998 on 2005-07-16
You can install the xplanet-images package if you want rather than downloading the pictures.

Good how-to - it was the not displaying background that I had missed previously.

---

### Post by Psycho275 on 2005-07-16
[QUOTE=mike998]You can install the xplanet-images package if you want rather than downloading the pictures.[/QUOTE]

I saw the package when looking for xplanet, but didn't mention it as I haven't tried it yet.

[QUOTE=mike998]Good how-to - it was the not displaying background that I had missed previously.[/QUOTE]

Thanks - It took me a little while to figure out how to hide the background. One problem with not allowing nautilus to control the desktop is that it will no longer show icons for removable devices on the desktop automatically, so I now use "Computer" through Nautilus instead to access it.

---

### Post by kleeman on 2005-07-16
To avoid losing my desktop icons I don't use the nautilus change you mention and use instead this script which works with gnome2

[http://stef.tvk.rwth-aachen.de/~nazgul/linux-hacks.php](http://stef.tvk.rwth-aachen.de/~nazgul/linux-hacks.php)

Great idea btw!

---

### Post by kleeman on 2005-07-16
Actually for some reason the script borks so ignore my previous post  ](*,)  ](*,)

---

### Post by kleeman on 2005-07-16
This one works better (you need python installed:


#!/usr/bin/env python

# Script for handling xplanet in Gnome
# Add this script to your "Startup Programs" in the "Sessions" control center applet

import sys, os, time, glob

def main(argv):
   #we use /tmp to store image files
   originalFilename = '/tmp/xplanet-original.png'

   if len(argv) > 1: #called in update mode
      # At this point, there will be a two images in /tmp
      # We'll delete the old one, and rename the new one
      for f in glob.glob('/tmp/xplanet-background-*.png'):
         os.remove(f)
      #filename includes a timestamp
      background = '/tmp/xplanet-background-%d.png' % int(time.time())
      #rename the newly generate image
      os.rename(originalFilename, background)

      #now set the background to the new image (by modifying your gconf database)
      os.system('gconftool-2 -t str -s /desktop/gnome/background/picture_filename "%s"' % background)
      return

   #called in startup mode, set up and start xplanet

   #set some options, change here to suit your desires
   options = '-geometry 1600x1200 -longitude -74 -latitude 41'

   #start xplanet niced
   #refresh every 5 minutes, sleep if inactive for 10
   #name output image, will get renamed
   #re-call this script in update mode after rendering a new image
   #run this in the background so the script will exit
   startxplanetcommand = '/usr/bin/nice -19 xplanet -wait 300 -hibernate 600 -output %s %s -post_command "handle-xplanet.py update" &' % 
   (originalFilename, options)
   os.system(startxplanetcommand)

if __name__ == '__main__':
   main(sys.argv)


You may wish to change the latitude and longtude if you don't live in New York  :razz: 

Then to get it to work:

sudo cp handle-xplanet.py /usr/bin

then (as above)

System > Preferences > Sessions
Click on the "Startup Programs" tab, and click on "Add". Enter "handle-xplanet.py" (without the quotes) into the "Startup Command" text box, and click OK

You may also need to reboot to eliminate previous xplanet instances.

Sorry to hijack the thread  :smile:  :smile:

---

### Post by Psycho275 on 2005-07-16
Thanks very much for that, kleeman - I'll give it a go tomorrow (it's getting late here!). Don't worry about hijacking the thread - it's useful information! ;)

---

### Post by Sephiriz on 2005-07-17
I don't believe your post maintained the necessary indentation required to run the Python script :(

Could you possibly provide it as a file?

Also this problem occurs:

```

  File "/usr/bin/handle-xplanet.py", line 36
    startxplanetcommand = '/usr/bin/nice -19 xplanet -wait 300 -hibernate 600 -output %s %s  -post_command "handle-xplanet.py update" &' %
                                                          ^
SyntaxError: invalid syntax

```

---

### Post by Psycho275 on 2005-07-17
[QUOTE=Sephiriz]I don't believe your post maintained the necessary indentation required to run the Python script :(

Could you possibly provide it as a file?

Also this problem occurs:

```

  File "/usr/bin/handle-xplanet.py", line 36
    startxplanetcommand = '/usr/bin/nice -19 xplanet -wait 300 -hibernate 600 -output %s %s  -post_command "handle-xplanet.py update" &' %
                                                          ^
SyntaxError: invalid syntax

```[/QUOTE]
 I came across that error too, Sephiriz. I discovered removing the percentage symbol (%) from the end of the line stopped the error occuring, but also seemed to stop the script working too.

---

### Post by kleeman on 2005-07-17
Sorry about that I tried to upload it directly and the uploader would only accept certain files. Anyway here it is as a zip file 

 move it (as root) to /usr/bin and also 

sudo chmod a+x  handle-xplanet.py

---

### Post by ponx on 2006-03-03
When I try and run xplanet I get the following:

Error: Can't open display
Exiting from getDisplay.cpp at line 47

I've tried that Nautilus thing, but that doesn''t fix it.

Any ideas...?

---

### Post by arrrghhh on 2007-12-24
> **ponx said:**
> When I try and run xplanet I get the following:

Error: Can't open display
Exiting from getDisplay.cpp at line 47

I've tried that Nautilus thing, but that doesn''t fix it.

Any ideas...?


i've got the same problem.  i am using kubuntu, but i had xplanet working previously.  i have a feeling something got messed up because i used the svn on the xplanet website first, then i tried to build from source, and now i'm trying the repo way... none so far have worked.

i had this working before on a previous install, but i didn't have to do anything to fix it - i never had this error before.  i have a feeling my system needs to be completely purged of anything xplanet - does anyone know a quick 'n' dirty way to do that?  thanks!

---

### Post by smartboyathome on 2007-12-24
I think that is because it was made for an OLD old version of nautilus.

---

### Post by arrrghhh on 2007-12-24
> **smartboyathome said:**
> I think that is because it was made for an OLD old version of nautilus.

i'm using kubuntu... no nautilus here.

---

### Post by taygan on 2008-02-17
I had this running great with the handle-xplanet.py script, but then "something" happened.  It will show when loading, but then I get the "no wallpaper" brown with nautilus.  I tired selecting "no wallpaper" again, and it shows xplanet when loading, but then the brown comes and covers it up... hmmm.. Id like to keep my desktop icons, but get rid of the background.

Ideas?

EDIT: AHA!  If I run xplanet (and handle-xplanet.py??) and let it run for 5 minutes, and THEN restart the computer, everything comes back.  I assume it's something about the 5 minutes refresh rate resetting things back to normal.  (Hey folks, you can keep all your desktop icons and nautilus if you use the handle-xplanet.py script)

---

### Post by Demosthenesaus on 2008-02-21
I have the gnome-script running fine and I have installed custom maps based on month of year from NASA, and even a grey fuzzy ball masquerading as the moon floats around the Earth.  Any idea how to

a) Turn grey fuzzy ball in to a real moon map
b) Have automatically updating cloud maps
c) Have automatically updating marker files for earthquakes, storms, etc

---

### Post by likeachild83 on 2008-03-04
> Next, we need to stop nautilus from controlling the desktop:
Applications > System Tools > Configuration Editor
In the Configuration Editor, go to apps > nautilus > preferences and untick "show_desktop".

I'm not seeing this at all. I've got xplanet running, I can see it when the computer boots up before my desktop kicks in, but I don't have a sub category called System Tools and can't figure out what to do. Any ideas?

**edit** Nevermind! I ended up having to type gconf-editor in the terminal and it opened up the Config. Editor and I was able to follow the rest of your directions. Thanks anyway!

---

### Post by mpchlets on 2008-04-20
I was having trouble using the sh script with compiz since the line:

gconftool -t str -s /desktop/gnome/background/picture_filename "$PREFIX$OUTPUT"

was for gnome and compiz did not like that command.

I commented it out with a # and added this line instead using dbus:

dbus-send --print-reply --type=method_call --dest=org.freedesktop.compiz /org/freedesktop/compiz/cube/screen0/backgrounds org.freedesktop.compiz.set array:string:"$PREFIX$OUTPUT"


if you need to activate dbus, go into System->preferences->advanced  desktop effect settings and then under Utility you will find dbus.

Just an fyi for anyone else struggling with this one.

Hope it helps someone.

---

### Post by gforster on 2008-05-11
I am not understanding how to use the cloud map. I found a script [here]("http://xplanet.sourceforge.net/clouds.php") but I have no idea what to do with it now. Anyone?

---

### Post by GrouchyGaijin on 2011-02-26
I'm running 10.10 and when I try to run xplanet I can see the earth in my conky only.  The regular background stays visible.  No conky not even a part of earth shows up.

I followed the instructions in the first post.

---

### Post by Temporary Saint on 2011-08-26
Having problems getting the clouds overlay to dsplay.  Using xplanet ver.1.2.1 under Linux Mint 9 (Ubuntu 10.4 Gnome).  I can retrieve the cloud overlay .jpg, but it's not displaying.  Have specified the location of the jpg in the default config file and in the overly-clouds file.  Tried specifying the file location in both the [default] and [earth] sections of the config file as well.

command used is:

xplanet -latitude 40 -longitude -75 -radius 50 -quality 100 -geometry 800x600 -fork -wait 1800 -config ~/.xplanet

Any help?

Steve

---

### Post by Sealand on 2011-09-28
I'm running the 11.10 beta and have had to change my script that sets the gnome background image to a live xplanet picture.  I use it as a sort of clock, but I don't currently use cloud maps or any other clever stuff except for the night image that you have to set in the config file.

The script is modified from the one found at [http://xplanet.sourceforge.net/FAQ.php#gnome2](http://xplanet.sourceforge.net/FAQ.php#gnome2), the important difference being that it is now necessary to use **gsettings** instead of **gconftool**.

--------

[FONT=Courier New]#!/bin/bash
# Original script found at [http://xplanet.sourceforge.net/FAQ.php#gnome2](http://xplanet.sourceforge.net/FAQ.php#gnome2)
# Add this script to System->Preferences->Sessions->Startup Programs

myName=$(basename $0)
logger -p user.debug "$myName woke up at $(date)"

# Check to see whether the parent process has died (user logged out)
if [ "$PPID" == "1" ]; then
    logger -p user.debug "$myName (PID $$) exiting at $(date)"
    exit
fi

# how long to sleep between drawings
sleep=295s

# screen size
geometry=1280x800

# the name of the desktop image
prefix=/tmp
base=xplanet
extension=png

# Alternate between two filenames
first=${base}1.$extension
second=${base}2.$extension

currentBackground=$(basename $(gsettings get org.gnome.desktop.background picture-uri) "'")

logger -p user.debug "$myName current background file name is $currentBackground"

# Set the name of the output file to be different than the current background
if [ "$currentBackground" != "$first" ]; then
  outputFile=${prefix}/$first
else
  outputFile=${prefix}/$second
fi

# Build the parameters (including the $outputFile and $geometry)
xplanetParams="-num_times 1 -output $outputFile -geometry $geometry -projection mercator -proj_param 75"

# The xplanet command
logger -p user.debug "$myName running xplanet $xplanetParams"
xplanet $xplanetParams | logger

# update Gnome backgound
gsettings set org.gnome.desktop.background picture-uri file://$outputFile

# Sleep for a while, then run myself again
sleep ${sleep} ; exec $0
[/FONT]

---

### Post by dcstar on 2011-09-29
This is my 10.04 version of the script that automatically gets your screen resolution and location from various Gnome settings.

Feel free to use those bits in your own scripts:

```
#!/bin/bash
#xplanet-gnome.sh shell script v1.1
#shows Earth on your Gnome desktop with current lighting conditions,i.e. day and night

DELAY=5m
PREFIX=~/
OUTPUT=.xplanet.png
#
[B]# These should extract your current screen resolution and location from your system
# The location is found from the Gnome Clock Preferences Location.
#
GEOMETRY=$(xrandr | grep '*' | head -1 | cut -b 4-12)
LONGITUDE=$(gconftool -g /apps/panel/applets/clock_screen0/prefs/cities | cut -f5 -d " " | cut -f2 -d "=" | sed 's/"//g' )
LATITUDE=$(gconftool -g /apps/panel/applets/clock_screen0/prefs/cities | cut -f4 -d " " | cut -f2 -d "=" | sed 's/"//g' )[/B]
#
#default is no projection,i.e. render a globe
#rectangular is the flat world map. also try ancient, azimuthal,  mercator,..
PROJECTION=rectangular

# This stuff is to prevent multiple instances running if you log out and log in again
lockfile=$HOME/.xplanet.lock

# Check if timestamp of lock file is older than boot time:
if [ -e $lockfile ]; then
  CDATE=$(date +%s -r $HOME/.xplanet.lock)
  BOOTTIME=$(cat /proc/uptime | cut -f1 -d" ")
  CTIME=$(date +%s)
  FTIME=$(($CTIME - ${BOOTTIME/.*}))
  #
  # If older then it is a leftover - so delete it!
  if [[ $CDATE -lt $FTIME ]]; then
   rm -f $lockfile
 fi
#
fi

if [ ! -e $lockfile ]; then
   # Delete lockfile if program receives command to end:
   trap "rm -f $lockfile; rm -f $PREFIX$OUTPUT; exit" INT TERM EXIT
   # and let's make one now....
   touch $lockfile
else
   # Lockfile exists for this user profile, get me outa here!
   exit
fi

if [ -z $PROJECTION ]; then 
xplanet -num_times 1 -output "$PREFIX$OUTPUT" -geometry $GEOMETRY -longitude $LONGITUDE -latitude $LATITUDE
else
xplanet -num_times 1 -output "$PREFIX$OUTPUT" -geometry $GEOMETRY -longitude $LONGITUDE -latitude $LATITUDE -projection $PROJECTION
fi

# Update Gnome backgound - this works in Ubuntu 9.04 & 10.04
gconftool -t str -s /desktop/gnome/background/picture_filename "$PREFIX$OUTPUT"
sleep $DELAY
rm $lockfile
exec $0
```

---

