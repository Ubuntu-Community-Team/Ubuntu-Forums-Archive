---
title: "inactivity screen blank and lock time issues"
date: 2015-04-25
forum: Ubuntu Development Version
---

### Post by Doug S on 2015-04-25
Hi All,

Note: Posting on "Ubuntu Development Version" on purpose, and based on the target audience I hope to reach, even though my issue now spans 3 development cycles.

I am still having issues with screen blanking due to inactivity, and screen lock. These issues started during the 14.04 cycle. on or about 2014.03.12 (March 12th, 2014).

What I am looking for is others experiencing the same issue.

I have entered a[ bug report]("https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1448535"), but I'll cut and paste some of the description below:

> Just to separate the variables, use a different "Turn screen off when  inactive for" time and "Lock screen after" time under "Brightness and  Lock" under "System Setting".

 Leave the system inactive.
The screen goes blank after the appropriate inactive period.
After the additional screen lock time (or immediately if it is set to  "When Screen turns off"), the screen turns back on and stays on,  forever.
However, just move the mouse and then the screen will blank after the  appropriate  inactive period, and this time, and subsequent times, it  will stay off.
Now, unlock the computer, and this whole sequence will repeat.


References:
Recall [this old thread]("http://ubuntuforums.org/showthread.php?t=2246601"), which for which a fix was released.
Recall [this old bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/1292041"), for which I was told my issue was different (and I still think it is related).

Note 1: I only run Ubuntu desktops as VMs, and wonder if that is perhaps the root issue.

---

### Post by motobeats on 2015-05-05
[COLOR=#000000]*I get the same thing with 15.04. Using NoMachine from my local Windows machine. Log into the 15.04 KVM, I changed the settings to 1 minute for screen off and 30 seconds for lock. Took a while to fully dim but once it was black it snapped back on after ~30 seconds and stayed on for over 10 minutes.*[/COLOR]

---

### Post by Doug S on 2015-05-06
Thanks for adding your information.
I would be interested in results from anyone else. I believe this to be some sort of timing race condition, and do not expect it to happen for everyone. If it doesn't happen for you, that is useful to know also.
> **motobeats said:**
> [COLOR=#000000]*Took a while to fully dim*[/COLOR]Yes, the very gradual dim thing was new as of a couple of cycles ago. The gradual dim takes significant CPU power.
 
On my system the screen coming back on costs 1.5 watts of processor package power, such that more power is consumed than if the screen was on but not locked. Weird.
I am now doing as jerrylamos mentioned in one of those threads I referenced, and have screen lock set to never. Ultimately, I would prefer to go back to screen lock after a time.

Note: in the attached graph, do not worry about the legend, that refers to something unrelated that I was working on. Just consider it to be 3 different runs of the same thing.

---

