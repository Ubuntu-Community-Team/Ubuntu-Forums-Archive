---
title: "My story with Lubuntu 14.04 amd64 with some problems and their solutions"
date: 2014-06-04
forum: Ubuntu, Linux and OS Chat
---

### Post by stealz on 2014-06-04
This is a list of problems and solutions I encountered while installing Lubuntu 14.04 on my system I thought I should share.
I did quite a bit of digging and trial and error to get this sorted, I hope it will help some folks and maybe be interesting for some developers as some of the problems seem to be fixed easily.

I might not have the average System, I run a Intel i5-3570K 3.4GHz rig with 2 Video cards, a NVIDIA GeForce GTX 580 and the onboard graphics chip Xeon E3-12000, and two sound cards a Xonar DGX CMI8786 and the onboard sound chip HDA-Intel PCH, and also sound output via HDMI over HDA-Intel - HDA NVidia
I run it with 2 monitors over the nvidia card right now but might add a third, i.e. a TV so 2 outputs will run over the geforce and the third over the internal chip, but we'll get to that later.

**Network Manager applet / icon not showing up**
A commonly known problem, the network manager applet isnt showing up.
to fix this run *lxsession-default-apps* or launch the '_Default applications for LXSession'_ under Preferences, go to autostart and add *nm-applet*
The underlying Problem is that the _core applications_ field _Network GUI_ where *nm-applet* should actually go doesnt store its value through reboot.

**Weird and limited Dual Monitor behaviour**
Lubuntu does by default run in clone mode when you plug in several monitors and the default tool only offers to turn one monitor on or off. 
The clone mode isnt very pretty either, because it either cuts off parts of the larger monitor, or only the area of the small monitor is usable and the large monitor has a border with only background that is not usable.
First I recommend installing ARandR by typing
```
sudo apt-get install ARandR
```
in a terminal, and running it with
```
ARandR
```
there you can set your dual monitors screens next to eachother or above and below etc.
If you found your prefered setup you can save it and if you want to use it by default at startup you can open the configuration file with leafpad (by default it is saved under ~/.screenlayout/ ), copy the line starting with "xrandr" and paste it in the _Default applications for LXSession_ under _core applications_ in the field _Xrandr_
A little note here, if you like the Clone View but want to scale one monitor to the other so they show the same content, you can add the --scale-from parameter, so the 2nd monitor would scale the content from the given resolution, i.e. if your VGA monitor runs at 1600x900 and your HDMI runs at 1920x1080 you could use one the following lines to shrink on the small monitor or grow on the large monitor:

```
# this increases the small monitor on the large monitor
xrandr --output VGA --auto --scale 1x1 --pos 0x0 --output HDMI1 --auto --scale-from 1600x900 --pos 0x0"
# this shrinks the large monitor on the small monitor
xrandr --output VGA --auto --scale-from 1920x1080 --pos 0x0 --output HDMI1 --auto --scale 1x1 --pos 0x0"
```

However, I was not satisfied with that solution, I wanted a keyboard shortcut to cycle through -> Only one monitor / Clone zoom view / Extended View / only the other monitor,
and it should be pretty generic so I could use it on a flash drive installation of Lubuntu, so I worte a script. cycle through all combinations of dual monitor settings between the connected monitors, even if you have 3 or more monitors connected.
It can be customized easily and layouts can be modified or added / removed

[ATTACH]253725[/ATTACH]

you can run your script with 
```
bash /path/to/your/cyclemonitors2.sh
```

and / or add a keyboard shortcut in ~/.config/openbox/lubuntu-rc.xml between the <keyboard></keyboard> tags:
```
    <!-- Cycle through active window modes like in windows -->
    <keybind key="W-p">
      <action name="Execute">
        <command>bash ~/scripts/cyclemonitors2.sh</command>
      </action>
    </keybind>
    <keybind key="W-S-p">
      <action name="Execute">
        <command>bash ~/cyclemonitors2.sh -r</command>
      </action>
    </keybind>
    <keybind key="W-C-p">
      <action name="Execute">
        <command>bash ~/scripts/cyclemonitors2.sh -d</command>
      </action>
    </keybind>
```
Note you should edit the path to your cyclemonitors2.sh according to your system.
This will alow you to cycle through monitor layouts with Super-P, cycle backwards with Super-Shift-P and jump to a layout number via a small slider with Super-Control-P

If you want to use the lxpanel on only one screen you can right-click it and set the width to one pixel smaller than the actual screen width, that way windows on the next screen can use the whole space, i.e. my monitor runs on 1920x1080, so I set it to 1919
if you run dual monitors with different resolutions you might want to consider putting the panel on the top of the screen, because it will otherwise be located at the bottom of the screen container which has the hight of the higher resolution monitor, and thus not be accessible on the smaller monitor.

**No Sound issues**
while alsamixer works nicely when having one soundcard and one output device, it did not at all work with several soundcards and output devices. It took me a while to find out that my having no sound had nothing to do with actual sound problems, but with the applications picking the wrong output. I couldnt figure out any way to set the default output device. 
Pulseaudio seemed very convenient and offers an easy way to  play sound on all outputs.

To get started, install the following packages:
```
sudo apt-get install pulseaudio paprefs pavucontrol
```
launch *paprefs *go to simultaneous output and activate it.
edit /etc/pulse/default.pa with leafpad
```
gksudo leafpad /etc/pulse/default.pa
```
at the bottom of the file look for the following and modify or add it so it says
```
### Make some devices default
set-default-sink combined
```
this will make sure your default output is the combined output.
comment out the lines 
```
### Automatically restore the volume of streams and devices
# load-module module-device-restore  
# load-module module-stream-restore 
# load-module module-card-restore
```
to stop pulseaudio from automatically restoring those settings

restart your system and try it out. If you get crackling sounds and distortion with your system there are two things you can do

start a terminal, type alsamixer, and check if you have a PCM setting on any of your sound outputs (cycle through sound cards with F6). If you have any make sure the setting is below 100%, for me 74% or -6.6 db did solve the distortion
I had problems with alsamixer resetting my sound volume on restart, so I had to do 
```
sudo alsactl store 0
sudo alsactl store 1
sudo alsactl store 2
sudo -H alsactl store 0
sudo -H alsactl store 1
sudo -H alsactl store 2

```
to save the alsa settings through reboot.

if you still get crackling, go back to /etc/pulse/default.pa find the line load-module module-udev-detect and add tsched=0 to it so it says
```
load-module module-udev-detect tsched=0
```

since I still had a few settings in alsa that wouldnt stick, I had to make a small script that launches at startup and sets my amixer settings the way I want them to be (i.e. select my front output for my internal soundcard, where my headphones are plugged in.

```
#!/bin/bash
sleep 10
DGX=$(grep 'DGX' /proc/asound/cards | awk '{ print $1 }')
HDA=$(grep 'HDA-Intel' /proc/asound/cards | grep -v 'NVidia' | awk '{ print $1 }' )
sleep 1
amixer -M -c $HDA sset PCM 74%,74%
sleep 1
amixer -c $DGX sset 'Analog Output' 'FP Headphones'
```
I had to set the DGX and HDA dynamically, because sometimes my soundcards would switch between slot 0 and 1 and then the settings wouldnt work. while these exact settings will probably not help you, it gives you an idea on how to set it up automatically. read *man amixer* and try *amixer -c # scontents*, where # is your card number starting with 0, to find the settings you need.

**qterm - Quake Console Style drop down terminal**
since every so often in Linux I use terminal commands I really like having a terminal that I can show and hide with a keypress that is easily accessible and can keep running in the background without closing.

to accomplish this I had to do a few things:

get wmctrl and xdotool: wmctrl will be used to position your window and hide it from the taskbar, xdotool will be used to find your mouse pointer position and show the quake terminal on the monitor the mouse is on.
```
sudo apt-get install wmctrl xdotool
```

if you're in amd64, edit your ~/.bashrc and look for the part where it says "If this is an xterm set the title to user@host:dir" and comment it out as follows:
```
#case "$TERM" in
#xterm*|rxvt*)
#    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
#    ;;
#*)
#    ;;
#esac
```

download my script and save it somewhere:
[ATTACH]253724[/ATTACH]

add a keybinding for the qterm: edit your ~/.config/openbox/lubuntu-rc.xml and add the following keybinding between the <keyboard></keyboard> tags:
```
    <keybind key="W-dead_circumflex">
      <action name="Execute">
        <command>bash ~/scripts/qterm.sh</command>
      </action>
    </keybind>

```
make sure to change the path to your path! 
If you want to use a different key and dont know how to call it launch *xev* and see what it spits out when you press it.
You're looking for the part that says  "(keysym 0xfe52, *dead_circumflex*)"

**A little rant on my behalf**
Lubuntu 14.04 is a LTS version, and those little bugs like the nm-applet not being stored in the appropriate spot, the poor choice of a monitor selection tool and alsamixer not storing its settings should really be looked into, as they hinder an otherwise very nice experience, especially if you want to run it on a laptop - considering quite a few people might be switching since windows xp is running out. I would look into it myself but my coding knowledge and time to get into the project are somewhat limited.
Other than that I really enjoy the fast response time and clean feel of Lubuntu. I hope my little tweaks will help someone out

---

### Post by monkeybrain20122 on 2014-06-04
Also you forgot update-manager not showing up.

To be honest, I think Lubuntu 14.04 is not fit for release. I was asked to replace XP on two old laptops. At first I planned to install Lubuntu, but after seeing the long list of bugs and experiencing quite a few in a first attempt to install I gave up, I didn't have all the time to look for and implement work arounds for things that should work out of the box. So I wiped the hard drive of lubuntu and installed Xubuntu instead. Haven't noticed any difference in performance but much less buggy (only mild complaint of xubuntu is its out of the box ugliness, but that can be fixed easily with a new theme, a different icon set and a nice wallpaper)

Thanks for the informative write up though, I am sure many people would find it helpful and it should be a sticky.

---

### Post by stealz on 2014-06-04
good point about the update manager. I run apt-get upgrade on a regular basis so I didnt really notice, but yeah that should really be fixed as well.
I will soon install some form of linux on some old laptops, so I will look into xubuntu, thanks for the hint.

Its a shame, since openbox seems really nice and flexible. I added a few keybinds for manual tiling among other stuff, not sure If I really feel like migrating again since I am set up now. 
Some problems when running with three monitors already announced themselves, I might be forced to switch. Oh well, we will see.

---

### Post by DrScum on 2014-07-12
I followed Stealz' procedure regarding installing ARandR and pulseaudio. After that the TV-Monitor attached via hdmi wasn't detected anymore. Does anyone know how to diagnose and solve this problem?
I am running Lubuntu 14.04 on a Tuxedo Laptop Graphics: Intel 4th Gen Gen Core Processor integrated graphics; Sound: Intel 8 Series /C220 Series High Definition Audio Controller.

---

### Post by nekomata2 on 2014-07-12
I'm using Lubuntu 14.04 and the LTS is still much better than Xubuntu 14.04 [(still with a bug in the menus that doesnt show all installed apps and other minor bugs)]("http://askubuntu.com/questions/466521/xubuntu-14-04-missing-settings-apps-in-whisker-menu")

---

### Post by DrScum on 2014-07-13
Regarding the HDMI problem (see above): in the meantime I found out (thread# 2166771) that apparently you have to boot with the HDMI cable attached. After doing that the HDMI output is available and the display works fine. From what I see on the pavucontrol should work too only there is no sound on the attached TV. Only if I select the built in audio output there is sound. If I combine the output as described by stealz there is no sound at all. This is where I am stuck at the moment.

---

### Post by sudodus on 2014-07-13
> **stealz said:**
> This is a list of problems and solutions I encountered while installing Lubuntu 14.04 on my system I thought I should share.
I did quite a bit of digging and trial and error to get this sorted, I hope it will help some folks and maybe be interesting for some developers as some of the problems seem to be fixed easily.

Thanks for sharing :KS
> 
**A little rant on my behalf**
Lubuntu 14.04 is a LTS version, and those little bugs like the nm-applet not being stored in the appropriate spot, the poor choice of a monitor selection tool and alsamixer not storing its settings should really be looked into, as they hinder an otherwise very nice experience, especially if you want to run it on a laptop - considering quite a few people might be switching since windows xp is running out. I would look into it myself but my coding knowledge and time to get into the project are somewhat limited.
Other than that I really enjoy the fast response time and clean feel of Lubuntu. I hope my little tweaks will help someone out

Some of the bugs, for example the Network Manager applet bug, are fixed when updated/upgraded today. These bug fixes will be included in the first point release Lubuntu 14.04.1 LTS expected to arrive in the end of this month (July). Then I think we'll consider this version of Lubuntu mature.

---

### Post by Bucky Ball on 2014-07-13
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request, but thanks for sharing.

---

