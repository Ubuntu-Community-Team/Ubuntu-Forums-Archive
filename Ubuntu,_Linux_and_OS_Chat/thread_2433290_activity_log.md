---
title: "activity log"
date: 2019-12-17
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-12-17
i know it is possible for a process to detect whether its human  interface (keyboard and mouse) is active since screensaver control can  do that and know that inactivity has been over some period of time and  launch a screen saver or screen lock.  i do not have any screen saver  enabled but i would like to get a log of times when there is activity.   maybe it's as simple as checking the interrupt counts for the keyboard  and the mouse and if they are the same between two times then there was  no activity for that period.  with X it may also simplify things in a  different by somehow showing activity levels without the need to find  the keyboard and mouse device.  so i think what i need is to know what  programs do that now to run a screensaver, lock the screen, or cut the  display off.  does anyone know what program or package i should should  look at (i would look at its source code)?

---

### Post by bernard010 on 2019-12-20
I may of found what you are talking about on Ask Ubuntu . How does script detect idle time?
[https://askubuntu.com/questions/202136/how-can-a-script-detect-a-users-idle-time](https://askubuntu.com/questions/202136/how-can-a-script-detect-a-users-idle-time)

Is this what you were referring to Bash log files ?

---

### Post by Skaperen on 2019-12-20
> **bernard010 said:**
> I may of found what you are talking about on Ask Ubuntu . How does script detect idle time?
[https://askubuntu.com/questions/202136/how-can-a-script-detect-a-users-idle-time](https://askubuntu.com/questions/202136/how-can-a-script-detect-a-users-idle-time)

Is this what you were referring to Bash log files ?

it's the right idea. but the programs the 2 answers give don't seem to work right.  these programs appear to be trying to catch events happening during a brief period that they are running.  what is needed is a program running in the background continuously that can catch all events and provide that info to other programs.  touching a file in ramdisk, per-user, might be a way to communicate the info without causing disk activity.  or maybe this needs to be integrated into the [COLOR=#0000cd][FONT=courier new]**lightdm**[/FONT][/COLOR] program.

---

