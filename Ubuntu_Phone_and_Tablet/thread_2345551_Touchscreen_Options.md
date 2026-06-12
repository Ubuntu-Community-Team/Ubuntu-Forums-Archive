---
title: "Touchscreen Options"
date: 2016-12-05
forum: Ubuntu Phone and Tablet
---

### Post by marcus.pearlman on 2016-12-05
I just got an Acer R11 Chromebook and installed Xumbuntu via crouton. The touchscreen support is surprisingly quite good (for linux) but I have one issue. It seems as though the default setting for touching the screen and moving your finger is the mousewheel. This is actually a great default setting for most applications, except when using Xournal, which is a stylus "handwriting" type app. I want to write on the screen and it instead scrolls the page via the mousewheel action. How can I change the settings? Is there a configuration like the synaptics touchpad one that I can alter? Thanks in advance

---

### Post by marcus.pearlman on 2016-12-05
Don't all respond at once, now :) 

So I am making progress on this issue. The "Driver" for the touchscreen is touchegg. I guess that is the default one for touchscreen support for Crouton. I am currently messing with the features there. Each touchscreen event is called a trigger, and the behavior is called an action. The Trigger I wish to change is "Drag," which default action is "scroll." Changing the action from scroll to Drag&Drop helped but is buggy in Xournal. Each time I draw a line, lift off the screen, and start to draw another line, each line is connected at the starting point of each line. In other words, drawing unwanted lines every time I start a new line. Annoying.

I bring this up so that anyone who has experience with touchegg can chime in and help. I will continue to work on this off an on, and post a solution if I find one.

---

### Post by wildmanne39 on 2016-12-05
This is an all volunteer global community in different time zones so the person that has the answer may not even have seen your post yet, it is okay to bump your thread once every twelve hours to keep it in view.
Thanks

---

### Post by marcus.pearlman on 2016-12-05
I'm patient, Wildman... I'm just updating the status of my problem. The "bump" is unintentional, as is this one... 

Running touchegg from the terminal, some debugging info can be viewed.  The error I think that causes the glitch is: GRAIL ERROR (touch.cpp:~Touch:82): touch 277 failed to be rejected. I'm assuming touch 277 is the previous touch? This error only occurs when clicking inside of Xournal.

Last update of the day, thanks.

---

### Post by marcus.pearlman on 2016-12-06
I solved the problem. The solution is to use touchegg for the touchscreen options. Touchegg seems quite good and works better than I thought it would. Steps to get it working.

[LIST]
[*]Install and setup touchegg
[/LIST]
[INDENT]```
sudo apt-get update
sudo apt-get install touchegg

```[/INDENT]

[LIST]
[*]Setup the configuration editor for touchegg
[LIST]
[*]Setup dependencies
[/LIST]
[/LIST]
[INDENT=2]```
sudo apt-get install build-essential libqt4-dev libx11-6
```
[/INDENT]

[LIST=|INDENT=2]
[*]Download and unzip the Touchegg-gce file
[*]install with the following commands
[/LIST]
[INDENT=2]```
qmake
make
```[/INDENT]

[LIST]
[*=1]my computer did not have qmake or make, so install that with:
[/LIST]
[INDENT=2] ```
sudo apt-get install qt4-qmake
sudo apt-get install make
```
[/INDENT]

[LIST]
[*=1]run touchegg from terminal
[*=1]open the config file: ~/.config/touchegg.conf
[LIST]
[*=1]note that my file was a shortcut to /etc/touchegg.conf so I had to edit that. touchegg could not edit that file, even runing under root. So I saved a local copy and copied it to that location
[/LIST]

[*=1]add a group for Xournal
[*=1]add a gesture with Gesture: drag, Direction: all, fingers: 1, Action: drag&drop
[*=1]log out and back in for the changes to work or you can kill touchegg and rerun it with
[/LIST]
[INDENT=2]```
sudo killall touchegg
touchegg
```
[/INDENT]

[LIST]
[*=1]running it a terminal like this shows the dialogue of what is going on, which may be helpful
[*=1]Xournal will now draw lines correctly but is very "buggy." An option in Xournal must be changed
[LIST]
[*=1]Options -> uncheck Use Xinput
[/LIST]
[/LIST]
[INDENT]
Now you can draw in Xournal. Note: the touchscreen support for various hardware may make any of these steps difficult. It seems that the developers are making progress because my touchscreen worked really right away. Some may have to mess with the /usr/share/X11/xorg.conf.d/50-synaptics.conf file or the 10-evdev.conf file. These files could also be located in /etc/X11/ xorg.conf.d/

Good luck[/INDENT]
[INDENT=2]
[/INDENT]

---

