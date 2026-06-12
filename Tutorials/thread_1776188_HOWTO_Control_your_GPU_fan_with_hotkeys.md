---
title: "HOWTO: Control your GPU fan with hotkeys"
date: 2011-06-05
forum: Tutorials
---

### Post by 2Karl on 2011-06-05
Hi Everyone,

My Nvidia GeForce 9800 GTX+ tends to run rather hot when I'm gaming and becomes unstable, sometimes hardlocking my machine. I used to work round this by underclocking the card, but nvidia-settings will no longer let me apply any clock settings (just snaps back to defaults when I click apply), so I thought of another way to improve stability.

One thing I've noticed is that although the drivers are supposed to dynamically control the GPU fan speed, they never seem to crank it up past the default idle speed of 35. I set the fan speed to 100 in nvidia-settings, but it's loud and distracting when I'm not playing games. I wanted a dynamic way of controlling my fan, so I wrote this script:

```
#!/bin/bash
current_speed=`nvidia-settings -t -q [fan:0]/GPUCurrentFanSpeed`
new_speed=0

case "$1" in

"up")	let "new_speed = $current_speed + 10"
	if [ $new_speed -gt 100 ]
	then
		new_speed=100
	fi
	eval "nvidia-settings -a [gpu:0]/GPUFanControlState=1 -a [fan:0]/GPUCurrentFanSpeed=$new_speed"
	;;
"down")	let "new_speed = $current_speed - 10"
	if [ $new_speed -lt 35 ]
	then
		new_speed=35
	fi
	eval "nvidia-settings -a [gpu:0]/GPUFanControlState=1 -a [fan:0]/GPUCurrentFanSpeed=$new_speed"
	;;
"min")	nvidia-settings -a [gpu:0]/GPUFanControlState=1 -a [fan:0]/GPUCurrentFanSpeed=35
	;;
"max")	nvidia-settings -a [gpu:0]/GPUFanControlState=1 -a [fan:0]/GPUCurrentFanSpeed=100
	;;
esac

exit 0
```
I saved it in ~/bin as "nvfanspeedadjust", but you can call it what you like. Once you've saved it, make it executable with: ```
 chmod +x ~/bin/nvfanspeedadjust
```

The script takes one argument and has 4 options:
[LIST]
[*]nvfanspeedadjust up: increases the fan speed by 10 (maximum 100)
[*]nvfanspeedadjust down: decreased the fan speed by 10 (minimum 35)
[*]nvfanspeedadjust max: sets the fan speed to 100
[*]nvfanspeedadjust min: sets the fan speed to 35
[/LIST]
Once that was all working, I went into Keyboard Shortcuts from the preferences menu and added four new shortcuts with the commands detailed above. I assigned them to the hotkeys Super+Numpad+ (Mod4++) for fan increase, Super+Numpad- (Mod4+-) for fan decrease, Super+Numpad/ (Mod4+/) for Fan Max and Super+Numpad* (Mod4+*) for fan min. Obviously you can assign them to whatever you like.

Now I have control over my GPU fan at any time, making it easy to crank it up before a gaming session with the max key and turn it off when I get back to the desktop, with a bit of fine tuning in between.

Hope some of you find this useful.

---

### Post by mbugno on 2011-06-08
Thank you for this Nvidia control set. Nvidia GPU drives me nuts on my laptop. Cooks and then the fan turns on.

Very much appreciated.

---

### Post by Jrx1216 on 2012-06-15
Sorry to revive an old thread. 

This works great with my Linux installs, but I'm not sure how I can convert this to my Windows 7/8 installs. Any chance someone would be able to help?
Again, sorry to revive a dead thread (and for Windows on an Ubuntu forum) but any help would be GREATLY appreciated!

---

### Post by PapaGary on 2012-06-15
Google WIndows 7 fan control gadget.

---

### Post by Statia on 2012-10-03
Sorry to revive an old thread.
It does not work on my system.
Trying to isolate the problem, I first try to set the speed manually from the command-line, using the same syntax as in the script.
(My fan runs continually on 60%)
 
```
$ nvidia-settings -a [gpu:0]/GPUFanControlState=1 -a [fan:0]/GPUCurrentFanSpeed=70
```This line terminates with no feed-back, usually on Linux a signal that the command has completed succesfully.
However:
```
$ nvidia-settings -t -q [fan:0]/GPUCurrentFanSpeed
60
```GPU: Nvidia GeForce GT430
driver version: 295.49
kernel: 3.2.0-31

---

### Post by Statia on 2012-10-03
Solved it.
Could you edit your HOW-TO to reflect my finding?
Before this script will work, you have to allow the fan setting to be modified.

In xorg.conf there an option needs to be added, like so:

```
Section "Device"
    
Identifier     "Device0"
       Driver         "nvidia"
       VendorName     "NVIDIA Corporation"
       BoardName      "GeForce GT430"
       **Option       "Coolbits" "4"**
  EndSection
```Next one has to start the nvidia-settings GUI, go to "Thermal Settings" and click on "Enable GPU fan settings".

After this the script will work.
(Maybe the script worked right away for older versions of the driver?)

---

