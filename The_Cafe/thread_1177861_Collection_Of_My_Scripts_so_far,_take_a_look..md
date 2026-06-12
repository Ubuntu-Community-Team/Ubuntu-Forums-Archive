---
title: "Collection Of My Scripts so far, take a look."
date: 2009-06-03
forum: The Cafe
---

### Post by altech6983 on 2009-06-03
[size=4]To use these scripts copy the code from the script's code window and paste in to a empty document and title it what you want. Then open up a terminal, navigate to the directory you put it in and type ./yourscriptname[/size]

[size=3][b]If you don't meet the requirements listed for the script you want, post before using the script and I will try to help you.

Most of these scripts can be modified quite easily so if you don't meet the requirements post and I may be able to help you[/b][/size]

[size=3]**All of these scripts run on this machine: Quad-Core 3.5GHz, 4GB RAM, ATI HD4870 X2 Video, 64 bit Ubuntu 8.10 Intrepid. This may or may not cause you trouble if your machine is different. Read the requirements, if you meet them then try the script, if it doesn't work post and I will try to help.**[/size]

[b][size=2][color=#FF0000]Any script I post should not harm your computer should you execute it wrong or it runs wrong, [/size][size=3]If I know or realize that you could harm your computer if it should do so I will post a [/size][size=5] big [/size][size=3] red warning telling you so.[/size][size=2]

That being said, I won't be held responsible for any trouble or damage you incur should you try to use my scripts. If you do have trouble I will try to help you resolve it.[/color][/size][/b]

----------------------------------------------------------------------------------------------------------------------------

I have written three or four scripts so far and I decided that I would post them here so that they might help someone else. They go in order that I wrote them. 

I have no set version system but in general it will go like this: If I deem it a small change the version will increase by 0.01, if it is a large change it will increase by 0.1. All scripts that I will post on here start out as a v1.0 .

Script 1 (v1.0):
This is the first script I ever wrote. This script launches Nexuiz among other things.

_**Requirements**_
[list]
[*]ATI Video Card (I run a HD4870 X2 so the fanspeed setting may not work for you if you don' have that card)
[*]That you use metacity for your compositing manager. If you need help with compiz just ask and I will see if I can find how to turn that one off. (If you don't know what you use and haven't changed settings, it is a good bet that it is compiz)
[*]That you have the main Nexuiz folder installed to /home/your-username/Nexuiz[/list]
**If you don't meet those requirements, post before using the script and I will try to help you.**

```
#!/bin/sh
#Creator:Albert Eardley
#Free to use this code however you see fit. If you use some of my code please credit me.

#Execute Nexuiz

#Turns Off mouse accleration
xset m 0 0

#Gets current values for all modified variables
fanspeed=`aticonfig --pplib-cmd "get fanspeed 0" | awk '/([0-9][0-9])/ {print $4}'`
metacity=gconftool-2 -g '/apps/metacity/general/compositing_manager'
screen=gconftool-2 -g '/apps/gnome-screensaver/idle_activation_enabled'

#Sets fan speed to 70%
aticonfig --pplib-cmd "set fanspeed 0 70%"

#Turns off metacity
gconftool-2 -s --type bool '/apps/metacity/general/compositing_manager' false

#Turns off screensaver
gconftool-2 -s --type bool '/apps/gnome-screensaver/idle_activation_enabled' 0

#Waits and then launches nexuiz
sleep 3
~/Nexuiz/nexuiz-linux-sdl.sh
sleep 3

#Sets everything back to what they were
aticonfig --pplib-cmd "set fanspeed 0 $fanspeed"
gconftool-2 -s --type bool '/apps/metacity/general/compositing_manager' $metacity
gconftool-2 -s --type bool '/apps/gnome-screensaver/idle_activation_enabled' $screen
```

Script 2 (v1.0):
This is a simple script that logs your cpu temp every ten minutes (easy to change to something else). I wrote it because I do overclocking and I just started folding and I wanted to see the max temp my comp went to while running two folding cores over night. It places the log in the your current working directory.

_**Requirements**_[list]
[*]That your cpu has sensor support
[*]You have installed the program lm-sensors[/list]

```
#!/bin/bash
#Usage, just run the script
#Requires that you have sensors installed and sensor support for your hardware
#Creator:Albert Eardley
#Free to use this code however you see fit. If you use some of my code please credit me.

while true; do #Run forever until Ctrl-C
	date +%r >> CPUTemp.txt #Appends date to file
	sensors | grep "Core" >> CPUTemp.txt #Appends temp to file
	sleep 10m #Waits ten minutes and does it again
done
```

Script 3 (v1.01):
I wrote this script because I wanted to be able to control the cores for folding and be able to control where the windows were placed.

_**Requirements**_[list]
[*]Two folding cores installed to the path /home/your-username/Folding and /home/your-username/Folding2
[*]That you run a Dual or Quad core machine
[*]That you have install wmctrl
[*]That you have at least two desktops (Not physical desktops like computers ;-) , virtual desktops)
[*]And that you use Gnome[/list]


```
#!/bin/bash
#This script controls my two Folding cores that I run.
#Usage, fahcontrol [start/stop/config] [core1/core2] [core2/core1]
#This script requires you to have wmctrl installed.
#This script needs to me placed in /usr/bin
#Creator:Albert Eardley
#Free to use however you see fit. If you use some of my code please credit me though.

if [ "$1" = "start" ]; then #If first argument is start then do start procedure
	if ([ "$2" = "core1" ] && [ "$3" = "core2" ]) || ([ "$2" = "core2" ] && [ "$3" = "core1" ]); then #Checks to see if both Cores should be started
		cd /home/altech6983/Folding #Changes working directory to Core1's script location
		gnome-terminal --title='FAHCore1' -x bash -c "./fah6 -smp -verbosity 9" #Launches a seperate terminal and bash to run Core1
		
		cd /home/altech6983/Folding2 #Changes working directory to Core2's script location
		gnome-terminal --title='FAHCore2' -x bash -c "./fah6 -smp -verbosity 9" #Launches a seperate terminal and bash to run Core2
		
		sleep 2 #Wait for windows to appear
		
		core1id=`wmctrl -l | awk '/FAHCore1/ {print $1}'` #Finds wmctrl id of the first Core
		wmctrl -i -r $core1id -t 1 #Moves Core1's terminal to desk2
		core2id=`wmctrl -l | awk '/FAHCore2/ {print $1}'` #Finds wmctrl id of the second Core
		wmctrl -i -r $core2id -t 1 #Moves Core2's terminal to desk2
		
		sleep 1
		wmctrl -i -r $core1id -e '0,0,20,800,435' #Moves Core1's window to top left corner
		wmctrl -i -r $core2id -e '0,0,487,800,435' #Moves Core2's window to below Core1's window
	
	elif [ "$2" = "core1" ]; then #Only launches Core1
		
		cd /home/altech6983/Folding
		gnome-terminal --title='FAHCore1' -x bash -c "./fah6 -smp -verbosity 9"
		
		sleep 2
		core1id=`wmctrl -l | awk '/FAHCore1/ {print $1}'`
		wmctrl -i -r $core1id -t 1
		
		sleep 1
		wmctrl -i -r $core1id -e '0,0,20,800,435'

	elif [ "$2" = "core2" ]; then #Only launches Core2
		
		cd /home/altech6983/Folding2
		gnome-terminal --title='FAHCore2' -x bash -c "./fah6 -smp -verbosity 9"
		
		sleep 2
		core2id=`wmctrl -l | awk '/FAHCore2/ {print $1}'`
		wmctrl -i -r $core2id -t 1
		
		sleep 1
		wmctrl -i -r $core2id -e '0,0,487,800,435'
	fi
elif [ "$1" = "stop" ]; then #If first command is stop do stop procedures
	if ([ "$2" = "core1" ] && [ "$3" = "core2" ]) || ([ "$2" = "core2" ] && [ "$3" = "core1" ]); then #Checks to see if both Cores should be stopped
		
		core1id=`wmctrl -l | awk '/FAHCore1/ {print $1}'` #Finds wmctrl id of the first Core
		wmctrl -i -c $core1id #Closes Core1
		
		core2id=`wmctrl -l | awk '/FAHCore2/ {print $1}'` #Finds wmctrl id of the second Core
		wmctrl -i -c $core2id #Closes Core2

	elif [ "$2" = "core1" ]; then
		
		core1id=`wmctrl -l | awk '/FAHCore1/ {print $1}'` #Finds wmctrl id of the first Core
		wmctrl -i -c $core1id

	elif [ "$2" = "core2" ]; then
		
		core2id=`wmctrl -l | awk '/FAHCore2/ {print $1}'` #Finds wmctrl id of the second Core
		wmctrl -i -c $core2id
	fi
elif [ "$1" = "config" ]; then
	if ([ "$2" = "core1" ] && [ "$3" = "core2" ]) || ([ "$2" = "core2" ] && [ "$3" = "core1" ]); then #Checks to see if both Cores should be configured
		cd /home/altech6983/Folding #Changes working directory to Core1's script location
		gnome-terminal --title='FAHCore1' -x bash -c "./fah6 -smp -configonly" #Launches a seperate terminal and bash to configured Core1
		
		cd /home/altech6983/Folding2 #Changes working directory to Core2's script location
		gnome-terminal --title='FAHCore2' -x bash -c "./fah6 -smp -configonly" #Launches a seperate terminal and bash to configured Core2
	
	elif [ "$2" = "core1" ]; then #Only configured Core1
		
		cd /home/altech6983/Folding
		gnome-terminal --title='FAHCore1' -x bash -c "./fah6 -smp -configonly"

	elif [ "$2" = "core2" ]; then #Only configured Core2
		
		cd /home/altech6983/Folding2
		gnome-terminal --title='FAHCore2' -x bash -c "./fah6 -smp -configonly"
	fi
fi
```

Leave a note if one of them helped you. Also if you have any question feel free to ask, I will try to help to the best of my knowledge. Thanks

---

### Post by monsterstack on 2009-06-03
You might want to tell people of some of the hardware-specific parts of your scripts and where the scripts need to be changed for others to use. Many people around here barely know any bash'n at all and will just copy-paste, get errors, and come back yelling WRRRRY. That's not something you want. :D

---

### Post by altech6983 on 2009-06-03
Okay I have post some requirements (all I could think of at this paticurlar time :-) )

Let me know if I missed some and thanks for pointing that out.

---

### Post by altech6983 on 2009-06-05
[size=3]**I have posted v1.01 of Script 3. The script now lets you pass the config argument so that you can configure your cores.**[/size]

---

