---
title: "When did Ubuntu fix the &quot;Suspend/Screensaver active when playing a video&quot; problem?"
date: 2014-12-02
forum: The Cafe
---

### Post by tjeremiah on 2014-12-02
I'll try to make sense of this and if I am late to the party..oops..Mind you, this was never a problem with VLC or default Gnome player.

I dont know if this is the best place to ask but one of the nuisances in Ubuntu for years is that when a video is playing whether it is flash or html5, if you have Suspend to activate before the video is finish playing (the video is 50mins long but you have suspend @ 10mins of inactivity), the computer would suspend or the screensaver would activate thus causing frustration. 

To help solve this applications such as Caffeine were created and a userscript that would kill the screensaver/suspend only when a video is playing in fullscreen or when the application is launched. The problem with the script is that it only worked when you played a video in fullscreen and Caffeine would work when the application was running. Even when the video stopped playing Caffeine would fail to notice that and your computer would be left on forever until you'd notice.

I am currently running an updated Ubuntu 14.04 and ive notice that this problem as been solved. When setting Suspend for 5 mins, whether I play a video in html5 or I use flash the computer would remain on until the video is finished playing almost like in Windows! Using Chromium with pepper flash, not Firefox.

Anyone know when this was implemented and how it was done?

---

### Post by pqwoerituytrueiwoq on 2014-12-02
EDIT:
your telling me it is fixed, which DE and what version?
Original post:
here is my script for stopping xscreensaver
this script should work with adobe flash videos, it does not work with html5 ones and i think chrome makes it act weird
this script is a service that works automatically requiring no user input, aside from determining the CPU usage threshold for adobe flash
it works with flash, chrome, parole, and emulationstation (that last one is a classic game UI for retroarch)
```
#!/bin/bash
me="`dirname $0`/`basename $0`"
#echo $me
if [ "$1" == "--help" ];then
    echo -e "Usage:\n\t`basename $0` [CPU TIMER] | --debug | --help\n\tCPU is the cpu usage usage for flash times 10 to assume video is running\n\tTimer is the amount of time to wait before checking if a video player is running"
    exit
elif [ "$1" == "--debug" ];then
    cpu="20"
    delay="5"
else
    if [ -z "$1" ];then
        cpu="20"
    else
        cpu="$1"
    fi
    if [ -z "$2" ];then
        delay="55"
    else
        delay="$2"
    fi
    if [ "`pgrep -f $me | wc -l`" -gt "2" ]; then
        echo "Already running..."
        exit
    fi
fi
while [ 1 ]; do
#    clear
    chrome="`pgrep -lf chrome | grep ppapi | awk '{print $1}' | paste -sd ','`"
    flash="`pgrep -f flashplayer | paste -sd ','`"
#    echo "chrome=$chrome"
#    echo "flash=$flash"
    if [[ -n "$chrome" || -n "$flash" ]];then
        if [ -n "$chrome" ] && [ -n "$flash" ];then
            flash="$flash,$chrome"
        elif [ -n "$chrome" ];then
            flash="$chrome"
        fi
#        echo "Flash processes: $flash"
        # multiply by 10 to remove decimal in newer versions of top
        flash=`top -bn 1 -p "$flash" | grep $USER | head -1 | awk '{print $9*10}'`
        if [ "$1" == "--debug" ];then
            echo "Flash is using `calc $flash/10`% CPU. Threshold is `calc $cpu/10`%"
        fi
    else
#        echo "No flash running"
        flash="0"
    fi
    if [[ $flash -gt $cpu || -n "`pgrep -f parole`" || -n "`pgrep -f emulationstation`" ]]; then
        xscreensaver-command -deactivate > /dev/null
        if [ `xset -q | grep -ce 'DPMS is Enabled'` -eq 1 ];then
            xset -dpms
            xset dpms
        fi
        echo "Video or flash is running, no screensaver for you"
    fi
    sleep $delay
done
```

i use this config for smplayer
```
cat .mplayer/config 
# Write your default config options here!
heartbeat-cmd="xscreensaver-command -deactivate"
```

for html5 content i have this toggle script
pass -t to it to make it toggle, - u is used with the xfce4-genmon-plugin, no argument tells you the status
```
#!/bin/sh
if [ "$1" = "-t" ];then
    if [ $(xdg-screensaver status) = "enabled" ];then
        arg1="suspend"
    else
        arg1="resume"
    fi
    arg2=$(xwininfo -root | grep 'Window id'|awk '{print $4}')
    xdg-screensaver $arg1 $arg2
elif [ "$1" = "-u" ];then
    echo "<tool>Screensaver</tool><click>toggle-screensaver -t</click>"
    if [ $(xdg-screensaver status) = "enabled" ];then
        echo "<img>/usr/share/icons/gnome/16x16/apps/xscreensaver.png</img>"
    else
        echo "<img>/usr/share/icons/gnome/16x16/devices/computer.png</img>"
    fi
else
    xdg-screensaver status
fi

exit
```

---

### Post by tjeremiah on 2014-12-02
Ubuntu 14.04 LTS using Chromium. I havent used Firefox yet but I would like to see if anyone else has experienced what I mentioned in the OP.

---

### Post by sisco311 on 2014-12-02
mplayer uses the XSS and/or the XResetScreenSaver API (if it's supported) to disable the screensaver . Not 100% sure about the other media players, but I think that they also use this APIs. 

> **pqwoerituytrueiwoq said:**
> 
i use this config for smplayer
```
cat .mplayer/config 
# Write your default config options here!
heartbeat-cmd="xscreensaver-command -deactivate"
```


mplayer defaults to the -stop-xscreensaver option which should disable the screensaver for you. I'm using mplayer SVN-r37224 and Xfce4 4.10 and it works for me. Which DE and version of mplayer are you using?

BTW, I'm working on a patch for mplayer to allow it to re-enable the screensaver when the video is paused.

---

### Post by tjeremiah on 2014-12-02
I just tried watching a long FLASH and HTML5 video in FIREFOX and the suspend activated :(.Watched the same video under Chromium and suspend waited till the video was finished playing. So I can only assume Chromium (Version 39.0.2171.65 Ubuntu 14.04 (64-bit)) is doing something right. Sorry for the false alarm but if im not the only one that is experiencing this under Chromium at least a browser is getting it correct. Maybe Firefox is next. Ill do more research to see why Chromium behaves.

---

### Post by pqwoerituytrueiwoq on 2014-12-02
> **sisco311 said:**
> mplayer uses the XSS and/or the XResetScreenSaver API (if it's supported) to disable the screensaver . Not 100% sure about the other media players, but I think that they also use this APIs. 



mplayer defaults to the -stop-xscreensaver option which should disable the screensaver for you. I'm using mplayer SVN-r37224 and Xfce4 4.10 and it works for me. Which DE and version of mplayer are you using?

BTW, I'm working on a patch for mplayer to allow it to re-enable the screensaver when the video is paused.
xfce 4.10 or 4.11
i've had that file for a long time now and assumed it was still needed
```
~$ mplayer --version
Unknown option on the command line: --version
Error parsing option on the command line: --version
MPlayer2 2.0-701-gd4c5b7f-2ubuntu2 (C) 2000-2012 MPlayer Team
```

---

### Post by help_me2 on 2014-12-04
My screen is set to turn off after 10min and it still turns off after 10min of watching a video. Was never a problem for me because when I see the screen start to fade, I hit the mouse or hit Enter. Voila, screen back. I thought this was normal fair.

---

### Post by mastablasta on 2014-12-04
well the system woul dneed to know you are playing a video and not some flash commercial that si going round and round while no one is at the screen.

---

### Post by tjeremiah on 2014-12-04
okay, ive done more testing and I think its due to the feature Google added to the browser that lets you know when audio is playing from a certain tab. I noticed that when audio isnt playing the suspend would kick in under chromium. When audio is playing whether it is a flash video or html5 then no suspend would happen during the video playing. 

I always thought about this but never knww how to implement it so this is directed to you developers. 

I always thought an audio feature should be put in that would help solve this problem like what I assume Google has done. If audio is above a certain LEVEL % disable suspend. When audio is @ 0, enable suspend. 

Thoughts?

---

