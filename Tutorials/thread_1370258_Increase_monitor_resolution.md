---
title: "Increase monitor resolution"
date: 2010-01-02
forum: Tutorials
---

### Post by sharaq on 2010-01-02
As this was a issue for most Karmic users I thought of writing this,  Hope this will help you guys. 

First open a terminal > Applications >> Accesories >> Terminalin the terminal type :
  ** 1) **  ```
 **$ xrandr**
```  (without the $ mark)
this will display the allowed resolutions
something like this :

> Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
**VGA1** connected 800x600+0+0 (normal left inverted right x axis y axis) 267mm x 200mm
   800x600        85.1* +
   640x480        75.0     60.0  
   720x400        70.1  
then type 
** 2)**   ```
 **$ cvt 1024 768**
```  (any resolution that you want similar to this)

the output will be similar to this :
> [B]# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync[/B]
[B]
3)[/B]```
** $ xrandr --newmode <Modeline>**
```  (copy the modeline of the previous output to the place mode line)
for example :```
**$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync**
```**4)  **```
**$ xrandr --addmode VGA1 1024x768_60.00**
```  (here for **VGA1** you have to use what ever that was there for** $ xrandr** output in **step 1**)

**5)** ```
 **$xrandr --output VGA1 --mode 1024x768_60.00 **
``` (replace VGA1 accordingly, **remember to use the numbers within inverted commas in step 3 , after --newmode for 1024x768_60.00**  )

***Running these would change your resolution but this is temporary.these steps were done to make sure that these commands work . After step 5 you should see the resolution change.If this is successful proceed to the next step 

 
**6)**
```
**$ sudo gedit /etc/gdm/Init/Default**
```(this will ask for your root password type the password and a text editor will appear)
in this you will see a text line like this 
> [B]PATH=/usr/bin:$PATH
OLD_IFS=$IFS
[/B]just below this paste the** step 3 to 5** commands
and then save it.

example :
> 
#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George

PATH=/usr/bin:$PATH
OLD_IFS=$IFS
[B]xrandr --newmode "1024x768"   70.00  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

xrandr --addmode VGA1 1024x768_60.00

xrandr --output VGA1 --mode 1024x768[/B]

if [ -x '/usr/bin/xsplash' ];

then
        /usr/bin/xsplash --gdm-session --daemon
this worked in karmic ......I think this will be helpful to you if you want know more about [**xrandr**]("https://wiki.ubuntu.com/X/Config/Resolution")


> If **step 6** isn't working then read this post by [COLOR="Red"]**mpatrick**[/COLOR]
[http://ubuntuforums.org/showthread.php?t=1364460&page=5]("http://ubuntuforums.org/showthread.php?t=1364460&page=5")
Thank you mpatrick..

---

### Post by AJH101 on 2010-01-04
This worked great for me - except that the resolution reverted after a restart! :-(

Even after I checked that I had entered the info as per the last step.

Any ideas?

Thanks!

---

### Post by innocenceisdeath on 2010-01-04
What if the resolution I need is higher than the maximum shown by xrandr?

---

### Post by Harry_Iyer on 2010-01-05
I don't think you can set a resolution higher than the max shown by xrandr - EVEN if you have the exact drivers for your gfx card . . . but I might be wrong

---

### Post by wizel on 2010-01-06
You can have a "virtual" resolution. Meaning the screen will scroll as you approach the borders.

I use this script to enable/disable between 1024x600 to 1024x768

```
#!/bin/bash

function pan-mode {
    echo `xrandr --prop | grep "current"`
    }

function pan-enable {
    echo Enabling VGA output
     xrandr --output LVDS1 --panning 1024x768
    }
function pan-disable {
    echo Disabling VGA output
     xrandr --output LVDS1 --panning 1024x600
    }

### MAIN ###
case $1 in 
    on)  pan-enable ;;
    off) pan-disable ;;
    status)  pan-mode ;;
    *)   echo "*usage: $0 on|off|status"    ;;
esac

```

---

### Post by AJH101 on 2010-01-07
I thought the whole point was that we are trying to ADD resolutions that may not be recognised as being available?

---

### Post by wizel on 2010-01-08
LCD (all portables and flat screens) can't display a higher resolution of what's designed.
They contain a fix number of pixels, so max resolution is determined by the physical device.
CRT (the old tube screen) can go basically to any resolution. Limitation is the card, as they don't have physical pixels, but a cathodic ray that can draw on the screen.

Hope it clarifies the difference between "real" resolution and "virtual" resolution.

---

### Post by AJH101 on 2010-01-08
*I do not dispute that - but I thought we were trying to add resolution that is possible, but not recognised. I ran Ubuntu *with a resolution of 1024x768 (so I know its possible) until an update and now the highest res I am told is available is 800x600. I can acgieve 1024x768 using the method above but have to do this each time I restart, despite the extra step above! :-(

---

### Post by wizel on 2010-01-09
AJH101 sorry, seems two different questions/answers are been discussed.
Regarding to resolution non available after boot, you may want to ensure /etc/gdm/Init/Default is executed properly. "gdm" has been chaged significantly with 9.10.
One way to verify is to add:
touch /var/tmp/some-file-that-doesnt-exist 
into /etc/gdm/Init/Default and see if the file  /var/tmp/some-file-that-doesnt-exist is created after reboot. 
If not, then /etc/gdm/Init/Default is not properly executed.

See [http://ubuntuforums.org/showthread.php?t=1306696](http://ubuntuforums.org/showthread.php?t=1306696)

---

### Post by AJH101 on 2010-01-09
Hmm very interesting. I confess however this is really beyond me. Do I have to add those two lines of code somewhere? Can I just add them onto the end of a file? I can follow instructions but they need to be v e r y s l o w a n d c l e a r :-) Thanks.

---

### Post by wizel on 2010-01-09
Edit the gdm default file:

```
sudo gedit /etc/gdm/Init/Default
```

Look at the end of the file for:
```

      fi
    fi
  fi
fi

exit 0
```

Add the touch command:
```
      fi
    fi
  fi
fi

**touch /var/tmp/testgdm**

exit 0
```

Reboot your computer and look for the  /var/tmp/testgdm if it exist:
```
ls -alg /var/tmp/testgdm
```

If the file doesn't exist, then the gdm default is not executed, meaning the code you have added from the first post is also not executed.

Pls note this is to verify the file  /etc/gdm/Init/Default is executed, so the coded provided in the first post is also executed.

---

### Post by AJH101 on 2010-01-09
OK now we are making progress. File does not exist! Now what? Thank you :-)

---

### Post by wizel on 2010-01-09
In fact, we're back to square one. What all that means is the proposed solution to add the xrandr command in /etc/gdm/Init/Default doesn't work. It doesnt mean the xrandr is not the right solution (it is), but the gdm did not get executed, so the added commands never got executed.

I'm not expert enough on how the gdm (gnome login system) works to provide you with a valid solution, but you may do the trick by adding the xrandr commands in an executable script that gets started after your login. This is not elegant, but may work.

To create a script file:

```
sudo gedit /usr/local/bin/increase_resolution.sh
```

then add to your file:
```

#!/bin/bash

xrandr --newmode "1024x768"   70.00  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

xrandr --addmode VGA1 1024x768_60.00

xrandr --output VGA1 --mode 1024x768
```

ensure you follow post 1 to define the exact xrandr command.

Then change the file to executable
```
sudo chmod +x /usr/local/bin/increase_resolution.sh
```

and you can execute to get the resolution changed.
You may add the script to the applications that starts with your session.

---

### Post by sharaq on 2010-01-10
yep!! guys **wizel** is correct, if step 6 is not working for you guys ,for some strange reason, just use a script as **wizel** has suggested and make it run at startup.
Thats what i did initially it works, but when you log in your resolution get changed and it just..... see for you selves.

go to 

> preferences >> startup applications -> add 

and add the script to the startup.remember to make it **executabe**.Right click the script file and go to permissions and check the make it executable box.

---

### Post by AJH101 on 2010-01-10
I did a bit more digging and (via Synaptoc) reinstalled gnome-session. A cold restart later 1024x768 is back up and running. Not sure which combination of steps worked but THANKS! :-)

---

### Post by wizel on 2010-01-10
I'm glad you've solved the issue. The gnome.session (the gdm part) was clearly broken as proved by the touch command.

For documentation purposes only, could you pls see if the /etc/gdm/Init/Default contais the xrandr commands by running:
```
grep xrandr /etc/gdm/Init/Default
```

---

### Post by AJH101 on 2010-01-10
This output does make reference to 1024x768. Thanks!

---

### Post by wizel on 2010-01-10
OK, so probably gmd was broken.

---

### Post by Tourdog on 2010-01-15
Wizel,
I seek your wize counsel!

My results are a "no go" on Sharag's method and so far the same with the "script".

I do not know how to do the correct steps after the 1st Sudo and the ad-hoc gedit comes up.   From that point what is the play-by-play?   What all goes into "terminal" just the 2 sudo's?  I have my own data for the   4 lines:
#!/bin/bash
xrandr ............
xrandr...............
xrandr................

Does the 4 lines above only go in the ad-hoc gedit or also in the terminal?

The 2 nd sudo goes only in the terminal?   In "startup applications"  I have never gotten the choice to "make the 4 lines of script from the ad-hoc gedit, executable" after pasting into the "Startup Applications menu".   
<br><br>Sure could use some counsel from anyone?!  :(

---

### Post by Tourdog on 2010-01-18
I finally solved the problem by using a script in "Startup Apps" by pointing to the xorg.config.   It works very well.....................  finally I have 1280 x 1024 at each boot-up automatically  (my monitor is a flat 19")

Thanks! :)

---

### Post by wayner9 on 2010-01-24
When I type the commands in step 1 of post 1 I don't get a display called VGA1 or anything like that - I just get "default".  Do I therefore use "default" in all of the commands shown in post 1?  I am having difficulty getting 1024x768 res on a new Ubuntu install.  This PC is also running Win7 (beta) which is able to run 1024x768 without problems on the same hardware so there shouldn't be an issue with capabilities.

---

### Post by sharaq on 2010-01-29
you should use **default**
I've mentioned about this in my post.

---

### Post by RRF2525 on 2010-02-22
Greetings --

I've been beating the web up on this one and found this thread this weekend.  I have worked through all the steps detailed but still no joy in acheiving 1680x1050.  Here's what I've done thus far:

1.  Installed Nvidia restricted drivers as recommended but machine will not boot to GUI
     (During boot the Ubuntu logo appears but screen goes black before desktop occurs and looses signal)
2.  I can successfully access console so that at least works -- rm xorg.conf from last step & 9.10 boots
3.  Following steps 1-4 all worked fine...here is the output of my modeline:

# 1680x1050 59.95 Hz (CVT 1.76MA) hsync: 65.29 kHz; pclk: 146.25 MHz
Modeline "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsyn

4.  On Step#5 I hit a snag...not allowed to peform the following:

 **$xrandr --output default --mode 1680x1050_60.00 **
     All I get is an error stating that the values are outside of limits (not those words - didn't jot down that error message -- sorry).

5.  Gnome is processing the gdm file as I can create a file that is not there on boot
6.  Although after doing all of the above steps I can force 1680x1050 to show in Display Preferences I cannot select it.  Doing so yields this error:

"The selected configuration for displays could not be spplied could not set the configuration for CRTC 99"

System information follows:  AMD X2 4200+ (Manchester)/Asus A8N/2G/250G/1TB w/dual NVIDIA 6800 GS (not-SLI enabled at this time) w/single 20" X20G-Naga III WSXGA monitor (1680x1050 59Hz 65KHz native resolution and vertical/horizontal freq.)  My monitor through all of this returns as "Unknown"

More digging has found the following:

1.  X.Org X Server 1.6.4 (2009-9-27)
2.  X Protocol (v11R0)
3.  Linux build is 2.6.24-23-server i686 Ubuntu
4.  xorg-server 2:1.6.4-2ubuntu4.1 (buildd@)

After installing the restricted 185 driver I get the following errors:

1.  the xorg.conf file generated by the installation of the 185 driver induces the error:
     "DefaultDepth not valid keyword"
2.  "Fatal server error - no screens found"
3.  "failed to initialize GLX extension (Compativle NVIDIA X driver not found)"
4.  "open /dev/fb0 (no such file or directory"
5.  I have to rm the xorg.conf file to boot to GUI and have tried this wilth even the latest d/l's from NV

I have tried to do as NV suggests in error messages and ran "nvidia-xconfig --mode-1680x1050" which will create a new xorg.conf file but always end with a loss of signal to monitor while booting to GUI and am forced to kill the machine and reboot to console to rm the xorg.conf file just created.

My questions are this...is 9.10KK simply unable to "understand" my monitor?  I had assumed that all my messing around porked the installation so I did backups and reinstalled but no joy...still doesn't work.

In the hopes this thread is still being monitored I'd be ever so appreciative to have a helping hand in getting my 16:10 back.  I can't take Windows for another day!!  : )

---

### Post by zezerbing on 2010-02-26
I have the same problem. I followed your steps and nothing happened. I did it a second time and nothing happened. xrandr shows an output of 1024x768. This is also in modeline. After step 4 (I think) it says res. should change, it didn't. When I reboot it goes into low graphics mode. A report says the res is 1024x768. why can't i change this??

---

### Post by Neo40 on 2010-02-27
Well, doesnt work with me.
I use nvidia driver. My LCD monitor (Daewoo HL711S) is able to use 1280x1024 but the max I get now is only 1024x768.

The command xrand gives:

eric@eric-desktop ~ $ xrandr 
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   576x432        57.0  
   512x384        58.0  
   400x300        59.0     60.0     61.0  
   320x240        62.0  


If I type cvt 1280 1024 I see:

eric@eric-desktop ~ $ cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

Then, you say: xrandr --newmode Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
 
and I get this:

eric@eric-desktop ~ $ xrandr --newmode Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>


What is wrong???

---

### Post by sharaq on 2010-02-28
if u are using nvidia drivers try to install the drivers using envyng...

using synaptic install **envyng-core**

then in a terminal type

```
sudo envyng -t
```

and uninstall any nvidia drivers installed and reinstall using envyng

---

### Post by oradano on 2010-05-21
worked!

I have a dell inspiron 1545 with external monitor in docking station.  The laptop display was working fine but external monitor wasn't configured and resolved to ugly 1024x768 lowres.

I applied this change, including the update to /etc/gdm/Init/Default to make it permanent, now I can boot using laptop display or external monitor and it's perfect (just like the windoze resolution from before)

thanks so much for posting your solution sharaq!

---

### Post by oradano on 2010-05-21
I just got this to work for 1280x1024, you have the right info, just check the command syntax, use xrandr --newmode to create a new named mode using the output from cvt 1280 1024, afterward reference the named mode in the --addmode and --output commands



QUOTE=Neo40;8892389]Well, doesnt work with me.
I use nvidia driver. My LCD monitor (Daewoo HL711S) is able to use 1280x1024 but the max I get now is only 1024x768.

The command xrand gives:

eric@eric-desktop ~ $ xrandr 
Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       50.0* 
   800x600        51.0     52.0     53.0  
   680x384        54.0     55.0  
   640x480        56.0  
   576x432        57.0  
   512x384        58.0  
   400x300        59.0     60.0     61.0  
   320x240        62.0  


If I type cvt 1280 1024 I see:

eric@eric-desktop ~ $ cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

Then, you say: xrandr --newmode Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
 
and I get this:

eric@eric-desktop ~ $ xrandr --newmode Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
usage: xrandr [options]
  where options are:
  -display <display> or -d <display>
  -help
  -o <normal,inverted,left,right,0,1,2,3>
            or --orientation <normal,inverted,left,right,0,1,2,3>
  -q        or --query
  -s <size>/<width>x<height> or --size <size>/<width>x<height>
  -r <rate> or --rate <rate> or --refresh <rate>
  -v        or --version
  -x        (reflect in x)
  -y        (reflect in y)
  --screen <screen>
  --verbose
  --dryrun
  --nograb
  --prop or --properties
  --fb <width>x<height>
  --fbmm <width>x<height>
  --dpi <dpi>/<output>
  --output <output>
      --auto
      --mode <mode>
      --preferred
      --pos <x>x<y>
      --rate <rate> or --refresh <rate>
      --reflect normal,x,y,xy
      --rotate normal,inverted,left,right
      --left-of <output>
      --right-of <output>
      --above <output>
      --below <output>
      --same-as <output>
      --set <property> <value>
      --scale <x>x<y>
      --transform <a>,<b>,<c>,<d>,<e>,<f>,<g>,<h>,<i>
      --off
      --crtc <crtc>
      --panning <w>x<h>[+<x>+<y>[/<track:w>x<h>+<x>+<y>[/<border:l>/<t>/<r>/<b>]]]
      --gamma <r>:<g>:<b>
      --primary
  --noprimary
  --newmode <name> <clock MHz>
            <hdisp> <hsync-start> <hsync-end> <htotal>
            <vdisp> <vsync-start> <vsync-end> <vtotal>
            [+HSync] [-HSync] [+VSync] [-VSync]
  --rmmode <name>
  --addmode <output> <name>
  --delmode <output> <name>


What is wrong???[/QUOTE]

---

### Post by iNaitvad on 2010-05-22
Then, you say: xrandr --newmode Modeline "1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync

that is wrong, it should be

```
xrandr --newmode 1280x1024 109.00 1280 1368 1496 1712 1024 1027 1034 1063

```

then

```
xrandr --addmode VGA-0 1280x1024
```

remember to change "VGA-O" to your correct outuput, you can get this with:

```
xrandr
```

---

### Post by habib2535 on 2010-05-23
Anyone can help me to progress here please ? i am stuck since 5 days on this :

I just installed the latest ubuntu 10.04 on a Toshiba-Tecra having "Trident Microsystems Cyberblade XP4m32" Monitor. After install resolution is defaulted to 800x600. I followed steps 1 to 4 above to increase the size (my laptop works with 1024x768 under XP). This was done OK and I obtained the resolution 1024X768 appearing in the drop list resolution options of the Monitor preferences but when I select the option if fails, or when I execute step 5
$ xrandr --output default --mode 1024x768_60.00
i got the message "xrandr : screen cannot be larger than 800x600 (desired size 1034X768)

when I re-execute the same command, I have "xrandr : Configure crtc 0 failed"

I saw a possible fix proposing to add
HorizSync 31.50-48.00
in Xorg.conf but I have no such a file in my /etc/x11/ or anywhere else in my installation ! (supposing that this will fix my problem !!!)

Thanks to help me to progress

---

### Post by arnabdatta on 2010-05-28
perfect!! Thank you soooo much! :)

---

### Post by sundays211 on 2010-06-25
after step 5, the message: 
```
xrandr: screen cannot be larger than 800x600 (desired size 1024x768)
```appears.
I know that this is not the case as this computer has always used 1024x768 before now, it has just started having these problems in 10.04. my monitor is an old CRT type, so it should support all screen resolutions anyway. sometimes my computer starts up as it should with the 1024x768 option, while sometimes it does not.

any help would be much appreciated as most web pages do not display correctly in 800x600 mode.

---

### Post by mhdbnoimi on 2010-12-30
After closing some game my display resolution turned into 640x480 so I tried to modify xorg.conf to the following but I noticed that there are disappeared sides (at right & left) in my monitor and fonts appear small and ugly!!!

**How can I fix this issue?**
----xorg.conf-----
```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 260.19.06  (buildd@yellow)  Mon Oct  4 15:59:51 UTC 2010

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 260.19.06  (buildmeister@builder101)  Mon Sep 13 04:59:45 PDT 2010

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
#    VendorName     "Unknown"
#    ModelName      "CRT-0"
#    HorizSync       28.0 - 33.0
#    VertRefresh     43.0 - 72.0
#    Option         "DPMS"

#    Identifier      "External DVI"
    Modeline        "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
    Option          "PreferredMode" "1360x768_60.00"

EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9500 GT"
EndSection

Section "Screen"

# Removed Option "metamodes" "nvidia-auto-select @1360x768 +0+0"
# Removed Option "metamodes" "640x480 @1360x768 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
#    Option         "TwinView" "0"
#    Option         "TwinViewXineramaInfoOrder" "CRT-0"
#    Option         "metamodes" "640x480 +0+0"
    SubSection     "Display"
        Depth       24
	Modes   "1360x768_60.00" "1024x768" "640x480"
    EndSubSection
EndSection


```


PS
I tried to change display resolution from display settings before modifying xorg.conf but I couldn't find any resolution bigger than 640x480 so I forced to change the resolution manually
Another thing, I tried the tip mentioned above  but it didn't work because I got the following error message:
```
mbnoimi@admino-mbnoimi ~ $ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1360 x 768, maximum 1360 x 768
default connected 1360x768+0+0 0mm x 0mm
   1360x768       50.0*    53.0  
   1024x768       51.0  
   640x480        52.0  
   800x600        54.0     55.0     56.0  
   680x384        57.0     58.0  
   512x384        59.0  
   400x300        60.0  
   320x240        61.0  
mbnoimi@admino-mbnoimi ~ $ cvt 1360 768
# 1360x768 59.80 Hz (CVT) hsync: 47.72 kHz; pclk: 84.75 MHz
Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
mbnoimi@admino-mbnoimi ~ $ xrandr --newmode "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
xrandr: Failed to get size of gamma for output default

```

---

### Post by mhdbnoimi on 2010-12-31
Any suggest guys

---

### Post by saimanoj on 2011-01-13
I installed Ubuntu 10.10 Meerkat. Then my screen resolution was 1024x768(19" screen)
It was acceptable.
Now, I updated my system using Update manager and after restarting and now it is 800x600.

I read all the posts in this thread and tried them

saimanoj@saimanoj-desktop:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0  

I am using an Nvidia Graphics card

saimanoj@saimanoj-desktop:~$ lspci|grep VGA
01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9400 GT] (rev a1)

---

### Post by donc786 on 2011-01-17
Thanks for the post. I can finally run higher than 1024x768 on a 19" monitor. I have a question that arose when messing with the /etc/gdm/Init file that is a little off topic, maybe someone could help point me towards the answer. It looks like some settings for the initial login (gdm?) are here. Is that correct? If so can they be changed to make the login box look different? I have found ways to change the colors and picture, but I would like to make the box either transparent or just the input box displayed without the rest of the stuff. Thanks again.

---

### Post by kOeTsU on 2011-02-13
```
koetsu@Thor:~$ xrandr --newmode &#8220;2048x1152_60.00&#8243;  197.97  2048 2184 2408 2768  1152 1153 1156 1192  -HSync +Vsync

koetsu@Thor:~$ xrandr --addmode LVDS1 2048x1152_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  33
  Current serial number in output stream:  34

```Im stuck here, please help me! :confused::confused:

I'm using ubuntu 10.10

---

### Post by ahkond on 2011-04-11
Today I woke up and turned on my ubuntu desktop to find that my large screen resolution was no longer available.  

I've tried the various solutions in this thread but they did not help.  

- xrandr says today that the maximum resolution is 1024x768 (yesterday I had a much higher resolution, probably 1920x1200).  
- reinstalling gnome.session made no difference
- attempting to install envyng-core using Synaptic Package Manager only leads me to believe that envyng-core does not exist (not found)
- running dpkg-reconfigure xserver-xorg (with gdm stopped) did not help

Yes, it's NVidia.  Everything worked fine yesterday, I did not install or alter anything, and today the machine is different.

---

### Post by MarkX on 2011-07-12
This is NOT SOLVED for most people here!!!!
Ubuntu and Diabol/Canon- ical are as ***t as ever at dealing with unrecognised monitors. FFS solve this problem properly!

---

### Post by MaxPayneFH on 2012-01-06
After inserting:

```
xrandr --newmode "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
```

on step 3 I get the following output:

```
xrandr: Failed to get size of gamma for output default
```

Is there any way to fix this ?

---

### Post by chome4 on 2012-01-07
> **MarkX said:**
> This is NOT SOLVED for most people here!!!!
Ubuntu and Diabol/Canon- ical are as ***t as ever at dealing with unrecognised monitors. FFS solve this problem properly!

You can write to them about this. Of all the problems I've had in two years of problem-free Ubuntu use, this is the one issue I can't resolve. I've no need for Windows but at least you get a full list of available resolutions to choose from. You can even use a dual-VGA card and it works perfectly, no need to edit/create files, open terminal and type code just to get your screen working properly.

Canonical Group Limited
 27th Floor Millbank Tower 
 21-24 Millbank
 London SW1P 4QP 
 United Kingdom


If you're not in the UK, find your local office here:


[http://www.canonical.com/about-canonical/contact/our-offices](http://www.canonical.com/about-canonical/contact/our-offices)

---

