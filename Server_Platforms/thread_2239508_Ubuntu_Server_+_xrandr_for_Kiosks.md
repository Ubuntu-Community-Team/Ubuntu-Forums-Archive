---
title: "Ubuntu Server + xrandr for Kiosks"
date: 2014-08-14
forum: Server Platforms
---

### Post by Anthony_DeNicola on 2014-08-14
I am putting together 100 kiosks for a client.  In those kiosks goes a 27 inch monitor that is positioned in portrait mode.  I have to rotate the Ubuntu window by 90 degrees (rotated right) in order for the display to show properly.  I am not using a graphical desktop but running chrome in an x session.

There are two things I am having trouble with: First, the monitors only seem to rotate about 1/2 of the time and it isn't consistent from kiosk to kiosk.  I need to get it to rotate every time a kiosk starts.  And second, I have a script that checks to make sure that it is rotated, however it seems like xrandr doesn't want to display it's status on all the computers (Intel Nuc's).    

Right now there are 52 of the 100 units where if I log in and type "export DISPLAY=0" and then "xranrdr" I get a "Can't open display 0".  I have tried this as root and I have tried it from the user who's account is running X.  On the other units if I type that it gives me the xrandr information for that display.  On the 52 monitors that I can't get xrandr information on, about 30 of them actually have the screen rotated right and the others don't have it rotated at all.

All these units are exactly the same in hardware, monitors, and software (images were burned to every one of them using a PXE server)

Here is what I have in my files:
/home/kiosk/init.rc
```

setterm -blank 0 -powersave off -powerdown 0 -cursor off -msg off
xset off
xrand -o left

```

/home/kiosk/.xsession
```


#!/usr/bin/env bash


xset -dpms; 
xset s off




# we get screen resolution


res=$(xrandr -q | awk -F'current' -F',' 'NR==1 {gsub("( |current)","");print $2}')
resx=$(echo $res | awk '{split($0,array,"x")} END{print array[1]}')
resy=$(echo $res | awk '{split($0,array,"x")} END{print array[2]}')


# starting xscreensaver


xscreensaver -nosplash &


while true; do 
  chromium-browser --incognito --window-size=$resx,$resy --window-position=0,0 --kiosk http://127.0.0.1/;
  sleep 5s;
done


#chromium-browser

```


/etc/cron.d
```

* * * * * kiosk /home/kiosk/screen-orientation.sh

```


/home/kiosk/screen-orientation.sh
```

#!/bin/sh
export DISPLAY=:0.0
rotation=`xrandr -q --verbose|grep HDMI1|cut -d ' ' -f5`
if [ "" = "right" ] ;
then
a = 1
else
xrandr -o right
fi

```

/etc/X11/Xsession.d/45customer_xrandr-settings
```


xrandr -o "right"
xset s blank
xset s 0

```

At this point I am not sure which files are even being read and which ones aren't .  I don't think the /home/kiosk/.init.rc file is being read as I can't find a reference for it anywhere (ex: /etx/X11/Xsession).  

If anyone has any insight on why I can pull up xrandr settings on some machines and not others or why the screen rotation isn't consistent throughout all my machines I would love to get your help.

Thanks!
Anthony

---

