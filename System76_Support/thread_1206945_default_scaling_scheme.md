---
title: "default scaling scheme"
date: 2009-07-07
forum: System76 Support
---

### Post by miniyak on 2009-07-07
I have the scaling option visible though tray. one thing in notice on full restart is that the default scheme is set to "On demand". This bugs me because typically i only use powersave, performance or press the "M" button for silent mode.

so, I have 3 1/2 questions

1: Is there a way to change the default power scheme on start up?

2: I have only noticed this on my s76 machine and not other jaunty installs, is this supposed to be a feature? Am I just being picky?

3: Benefits/disadvantages of On demand?

---

### Post by thomasaaron on 2009-07-08
I think all of your questions are answered here...

See last section of...
[http://ubuntuforums.org/showthread.php?t=597998](http://ubuntuforums.org/showthread.php?t=597998)

---

### Post by miniyak on 2009-11-26
Come to find out on-demand is the default scaling scheme for laptops

which is annoying considering i use my laptop as a portable desktop most of the time. (if that means anything now and days)

I recall looking into this issue for a couple of hours way back when but I never figured out how to solved the problem because it was easer to just live with it.

Unfortunately in 9.10 this issue has turned into a complete waste of time because all of a sudden ubuntu wants me to have admin privileges to change the scaling scheme 

Is there a way I can set Performance as the default or bypass the password prompt? ( ill look at the link again but i'm not sure i could figure out what was going on there)

---

### Post by thomasaaron on 2009-11-27
Read the last five or six paragraphs of this...
[http://hubpages.com/hub/Ubuntu--CPU-Scaling--Battery-life-and-You](http://hubpages.com/hub/Ubuntu--CPU-Scaling--Battery-life-and-You)

---

### Post by miniyak on 2009-11-27
the linked solutions seem like they probably worked in 8.04 or 8.10 but they don't seem to do anything for 9.04 or 9.10

I cant find the cpu-frequency monitor folder in the gconfig-editor, according to one of the comments at the second link provided, its suppose to just stick on reboot in 9.04. 

On start up in my install of 9.04 the last frequency does stick at the last scheme i used but resets to on-demand after a minute or so.

"sudo dpkg-reconfigure gnome-applets" which is the command that is suggested to disarm the administrative privileges need to change scaling setting doesn't seem to do anything noticeable in 9.10. 

In 9.10 i can't find the gconfig entry for cpu scaling ether.

I'm probably overlooking something?

---

### Post by keithce on 2010-01-20
BUMP!

I am having the exact same issues as miniyak.

---

### Post by thomasaaron on 2010-01-20
Does this help...
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1366896](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1366896)

---

### Post by patchwork on 2010-01-20
The package cpufrequtils allows you to set the default scaling option, using the cpufreq-set -c [cpu #] -g [governor setting, i.e ondemand, performance...] This seems to work for 9.10, though I've not tested it with 9.04.  EDIT: I suppose if I read all the way down the last link I could've avoided double posting.  Sorry for that.

---

### Post by miniyak on 2010-01-21
funny someone bumped this thread i just fix this a couple of days ago and was about to come back to it. Other solutions have been suggested but just to make things clear here is what worked to for me. Pretty sure Tom is pointing to the same thread where this was suggested

open the terminal then copy&paste

```
gksudo gedit /etc/init.d/ondemand

```
on line 27 change to the governor you want, then save (only one word needs to edited in this file)

---

