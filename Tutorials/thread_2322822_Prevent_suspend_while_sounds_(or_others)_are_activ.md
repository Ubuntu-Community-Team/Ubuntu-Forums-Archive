---
title: "Prevent suspend while sounds (or others) are active"
date: 2016-04-30
forum: Tutorials
---

### Post by hexaq2 on 2016-04-30
**Premise**: I like to have the system suspend itself when idle for few minutes (configure it in *System settings *-> *Power*)
**Issue**: If I play some music (for example in youtube) or other sources (wine games, native games, etc), and I go away for a bit, the system sees no keyboard/mouse input and suspends. This can cause issues ranging from no music (sadface) to various game problems, disconnects, etc.
**Workaround**: Hack a horrible script to poke the keyboard periodically and 'keep awake' the system while sound is playing, or <any> download is active, or system does a big update
**Inspiration**: [http://ubuntuforums.org/showthread.php?t=1423030](http://ubuntuforums.org/showthread.php?t=1423030) [http://ubuntuforums.org/showthread.php?t=2232064](http://ubuntuforums.org/showthread.php?t=2232064) and various others across the web
**Prerequisites**: xdotool. Also script was tested and debugged on unity 7 


Check if *xdotool *is installed, and make a new directory called scripts in your home. To open a terminal I use: ctrl-alt-t 
```
 
mkdir $HOME/scripts
sudo apt-get install xdotool

```

*xdotool* can simulate a key press, among other things, which then the system interprets as user activity, thus preventing the suspend.

Open your text editor (**gedit** is nice. Don't use libreOffice for this, you need to save a plain text file), and paste the below script, then save it in the "**scripts**" folder you made in your home as **sound_block_sleep.sh **(name is not really important, this is just what I used). Alternatively, can paste the following in a terminal:
```

gedit $HOME/scripts/sound_block_sleep.sh

```

If you care about the download bit, don't forget to check it's actually doing it's stuff (start a big download and wait for the system to see if it suspends). If you have issues check in the relevant script section for a possible fix.
 Script for pasting: 
```

#!/bin/bash
sleep_period=120s 
#the script will loop every 2 minutes (120seconds), and if the conditions are satisfied, it will trigger user input. CAUTION: do not make the sleep_period larger than the suspend period specified in power options, or the script may not function properly.
while true; do
#******sound checking*******
      sound_active="`cat /proc/asound/card*/pcm*/sub*/status | grep RUNNING | awk 'FNR==1{print $2}'`" 
     check="RUNNING"
    unitycontrolC="`ps -e | grep unity-control-c | awk '{print $4}'`" # **<- strange thing, when the sound config panel in unity is active (you are making changes to it and leaving it open), it puts the sound system in "Running" state, thus tricking the script into thinking the sound is active while it is not. I'm auto-closing it down in 2 minutes.**
    unitycontrolC_Check="unity-control-c"
    if [[ "$check" = "$sound_active" ]]; then 
        if [[ "$unitycontrolC" = "$unitycontrolC_Check" ]]; then
            echo "Granting 2m grace period for doing unity sound configs" && sleep 120 && `pkill -f unity-control-c`
        fi
                  xdotool key Num_Lock && echo "Holding awake due to sound" && xdotool key Num_Lock # <- **this presses twice on num-lock, within a few milliseconds. **
            else
        echo "Sound not running, keep awake condition bypassed" 
    fi

#******check if apt-get is running*******
    apt_active="`ps -e | grep apt-get | awk '{print $4}'`" 
    check="apt-get"
    if [[ "$check" = "$apt_active" ]]; then 
        xdotool key Num_Lock && echo "Holding awake due to apt-get activity" && xdotool key Num_Lock
        else
        echo "Apt not running, keep awake condition bypassed" 
    fi


#********downloads running*********
home=$HOME
script_path=$home/scripts/RX
file="$script_path"  
read -d $'\x04' record < "$file"  # <- on first run, this comand will fail since the "**RX**" file is not yet created by the below line. It will not fail the second time the script loops.
ifconfig | grep RX | awk 'FNR==2 {print $2}' | cut -d':' -f2,2 &> $script_path

now=`ifconfig | grep RX | awk 'FNR==2 {print $2}' | cut -d':' -f2,2`# <- If the script does not see downloads running, then delete this line, and delete only the "**#**"  from the line below. It means this script line didn't 'catch' your main  network card (it is setup to see the traffic from the first network  card listed by 'ifconfig'). If it failed, you do not need it, you need to activate and customize the below line:

**#** now=`ifconfig **eth0 **| grep RX | awk 'FNR==2 {print $2}' | cut -d':' -f2,2`  #  <- change "**eth0**" to your own network card name given by a "ifconfig" command in the terminal, for example mine is enp4s0 ("**lo**" is NOT it).


down_traffic=$((now-record))
    if ((down_traffic > 5500000 )); then
        xdotool key Num_Lock && echo "Holding awake due to downloads running" && xdotool key Num_Lock
    else
    echo "Not enough net traffic to keep awake"
fi
#***************************

sleep ${sleep_period}
done


```

Save and exit from the text editor.

Now to make it executable, you can open it's properties in **files** and check the "is executable" check-box in the second tab, or you can use the command line:
```
 
chmod +x $HOME/scripts/sound_block_sleep.sh

```


What remains is to execute it at log-on. This can be done by:
search in Dash for: startup
you should see "Startup applications" icon. Open it.
ADD new 
in the window that opens you have 3 fields:

**Name**: whatever you like
**Command: **bash -c 'sleep 10 && /home/**hex**/scripts/sound_block_sleep.sh'
**Description**: whatever you like

****
The command line above makes the script wait 10 seconds for the desktop to 'settle' after logon.
**Caution**: you need to put the full path to the script, that means the bold part from the Command line must be your user name (case sensitive).

Reboot

You can see the script activity in the system log:

```

less /var/log/syslog

```
"q" exits from the "less" command. Don't forget to scroll down for the last log lines, I simply press "END" on the keyboard and take it from there.

---

### Post by DanglingPointer on 2016-11-08
Hi hexaq2
Have a look at this program I created on launchpad it may be useful for you as an alternative.  It monitors cpu, network traffic and user-activity (mouse and keyboard); you give it minimum parameters for all of them or use the defaults.  Written in python3...
[https://launchpad.net/keep.awake](https://launchpad.net/keep.awake)

---

