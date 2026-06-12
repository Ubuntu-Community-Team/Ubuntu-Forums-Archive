---
title: "I made some scripts for everyone's convenience!"
date: 2013-05-05
forum: The Cafe
---

### Post by linuxvstheworld on 2013-05-05
I made a couple of simple installation scripts to install some programs, one is to install either Oracle Java or Open JDK, and the other is to install Skype 4.0, which a lot of people like!

The Java Installer Script is* [here ]("http://pastebin.com/kCPet1F2")*
And the Skype Installation Script is *[here]("http://pastebin.com/bCXWF5U9")*
Keep in mind that you will need to give the scripts executive permission by doing ```
chmod +x whateveryounameit
```
Enjoy! Let me know if it doesn't work on an OS based off of Ubuntu (Linux Mint, Xubuntu, etc.)

---

### Post by linuxvstheworld on 2013-05-08
Please post what 'based off' distros they work with, just to help certain people here know, and list any issues implying there are any.

---

### Post by ikt on 2013-05-09
Fantastic thanks :)

---

### Post by montag dp on 2013-05-17
Here's a script I just put together to automatically change the wallpaper in Gnome Shell.  I think it will also work in Ubuntu if Unity uses gsettings for the wallpaper (which I think it does?). Someone's probably done this before, but here it is.  You run it as:

```
./wallpaper_switcher.sh $time
```

where $time is the amount of time to wait in minutes before switching the wallpaper.  In the script, you will also need to change $dir to the directory with the pictures you want to use as a wallpaper.  You can set up this script to run on startup, of course.  The script will select a picture at random every $time minutes from the available files in the directory you specified.

I figured this thread was as good as any to post this, but let me know if there's a better place.

```
#!/bin/bash

# Wait time specified in minutes
time=$1


dir=/home/dprosser/Pictures


# Get list of pictures and number of pictures
npic=1
while read line; do
  pic[$npic]="$line"
  npic=`expr $npic + 1`
done < <(ls $dir)
npic=`expr $npic - 1`


# Change picture every however often is requested
I=1
while [ $I -lt 2 ]; do


# Select a random picture from the list
number=$[ ( $RANDOM % $npic ) + 1 ]


# Change the wallpaper
gsettings set org.gnome.desktop.background picture-uri file://${dir}/${pic[$number]}


# Wait awhile
sleep ${1}m


done
```

---

### Post by linuxvstheworld on 2013-05-17
> **montag dp said:**
> Here's a script I just put together to automatically change the wallpaper in Gnome Shell.  I think it will also work in Ubuntu if Unity uses gsettings for the wallpaper (which I think it does?). Someone's probably done this before, but here it is.  You run it as:

```
./wallpaper_switcher.sh $time
```

where $time is the amount of time to wait in minutes before switching the wallpaper.  In the script, you will also need to change $dir to the directory with the pictures you want to use as a wallpaper, $npic to the number of pictures you have, and the names of the pictures in the array $pic.  You can set up this script to run on startup, of course.  The script will select a picture at random every $time minutes.

There's probably a more automated way of doing this, but this works for me!

I figured this thread was as good as any to post this, but let me know if there's a better place.

```
#!/bin/bash 

# Wait time specified in minutes 
time=$1 

# Directory containing pictures
dir=/home/dan/Wallpaper_slideshow 

# Number of pictures
npic=16 

# Picture names
pic[1]=DSCN0844.JPG 
pic[2]=DSCN0859_rotate.JPG 
pic[3]=DSCN1604.JPG 
pic[4]=DSCN2882.JPG 
pic[5]=DSCN3059.JPG 
pic[6]=IMG_0837.JPG 
pic[7]=IMG_1377.jpg 
pic[8]=IMG_1619_cropped.JPG 
pic[9]=IMG_1619.JPG 
pic[10]=IMG_1644.JPG 
pic[11]=IMG_1664.JPG 
pic[12]=IMG_1670.JPG 
pic[13]=IMG_1699.JPG 
pic[14]=IMG_1950.JPG 
pic[15]=IMG_1960.JPG 
pic[16]=IMG_2302.JPG 

# Change picture every however often is requested 
I=1 
while [ $I -lt 2 ]; do 

# Select a random picture from the list 
number=$[ ( $RANDOM % $npic ) + 1 ] 

# Change the wallpaper 
gsettings set org.gnome.desktop.background picture-uri  file://${dir}/${pic[$number]} 

# Wait awhile 
sleep ${1}m 

done 
```
It's fine, people can post their scripts here, I don't mind. :D

---

### Post by montag dp on 2013-05-20
Just a heads-up, I improved my script above so that it automatically reads in the list of pictures in the directory you specify.  So now all you have to do is specify the correct directory in the script and it will automatically populate the list and figure out the number of pictures for you.

As a word of caution, if you do have other files in the directory that are not pictures, it will include those in the list as well.

---

### Post by montag dp on 2013-06-18
Here's another one.  Every time I want to watch a video, I find myself going into the power settings and changing it so the screen stays on and it doesn't suspend automatically.  Then I change it back when I'm done watching.

I decided this is inconvenient, so I made a script to do it.  Run it as:

```
power_toggle.sh $CLO
```

where $CLO may be -off, -on, or none specified.  -off will turn these power saving settings off so you can watch movies, etc, and -on will turn them back on when you are done.  If no CLO is specified, it will toggle the power settings; e.g. it will go from off to on or vice-versa. 

Here is the script.  The settings for -on mode are specified in seconds and may, of course, be modified.

Note that this only works for DEs that use gsettings, which means not KDE.

```
#!/bin/bash

# This script automatically changes power settings, so that the screen will
# not turn off and the computer will not suspend e.g. when user wants to watch
# video.  


# Input argument: 'off' or 'on'.  If no input argument is specified, then
# will toggle power saving mode - the opposite of the current setting.


################################################################################
### Settings


# Idle time until turning off the screen (seconds)
# Only use one setting here because GUI version only has one
sleep_time=180


# Idle time until suspending (seconds) (0 means never)
suspend_bat=300
suspend_ac=0


################################################################################


# Path in gsettings
gsetpath=org.gnome.settings-daemon.plugins.power
gsetpath1=org.gnome.desktop.session


# Check value for screen turnoff
cur_sleep_bat=`gsettings get $gsetpath sleep-display-battery`
cur_sleep_ac=`gsettings get $gsetpath sleep-display-ac`


toggle=$1


# Determine whether to switch on or off
if [[ "$toggle" == '-off' || "$toggle" == "-OFF" || "$toggle" == "-Off" ]]; then
  switch='off'
elif [[ "$toggle" == '-on' || "$toggle" == "-ON" || "$toggle" == "-On" ]]; then
  switch='on'
else
  echo
  echo "-on or -off not specified: will toggle power savings mode."
  if [[ $cur_sleep_bat -gt 0 || $cur_sleep_ac -gt 0 ]]; then
    switch='off'
  else
    switch='on'
  fi
fi


# Toggle power saving on or off
echo 
if [ "$switch" == 'off' ]; then


  echo "Switching off power saving mode"
  notify-send "Switching off power saving mode"


# Time until screen turns off (0 is never)
  gsettings set $gsetpath sleep-display-ac 0
  gsettings set $gsetpath sleep-display-battery 0 


# Time until suspend (0 is never)
  gsettings set $gsetpath sleep-inactive-ac-timeout 0
  gsettings set $gsetpath sleep-inactive-battery-timeout 0


# Turn off dimming of screen
  gsettings set $gsetpath1 idle-delay 0
  gsettings set $gsetpath idle-dim-ac "false"
  gsettings set $gsetpath idle-dim-battery "false"


else


  echo "Switching on power saving mode"
  notify-send "Switching on power saving mode"


# Time until screen turns off (0 is never)
  gsettings set $gsetpath sleep-display-ac $sleep_time
  gsettings set $gsetpath sleep-display-battery $sleep_time 


# Time until suspend (0 is never)
  gsettings set $gsetpath sleep-inactive-ac-timeout $suspend_ac
  gsettings set $gsetpath sleep-inactive-battery-timeout $suspend_bat


# Turn on dimming of screen
  gsettings set $gsetpath1 idle-delay $sleep_time
  gsettings set $gsetpath idle-dim-ac "true"
  gsettings set $gsetpath idle-dim-battery "true"


fi
echo                           

```

---

### Post by FrMartin on 2013-06-19
helpful work I think. thanks for sharing.

---

### Post by montag dp on 2013-06-19
> **FrMartin said:**
> helpful work I think. thanks for sharing.Thanks!  I think I will be using this a lot, so I put it in /usr/bin so I can run it with ALT+F2.

---

### Post by montag dp on 2013-06-22
If anyone is using that script, just FYI it's been updated.  I couldn't get it to work reliably at first.  It turns out there is a setting in org.gnome.desktop.session which needs to be changed in addition to the ones in  org.gnome.settings-daemon.plugins.power in order to keep the screen from dimming (at least on Gnome 3.8 - it's possible this might be desktop dependent).  Now it works well for me.  I just run it once to disable the screen turning off, suspending, etc., and again to turn those things back on.

If anyone else is using the script, could you let me know if it's working correctly for you?

---

