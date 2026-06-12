---
title: "screen blanks when idle for 10min, despite all attempts to prevent it"
date: 2015-01-27
forum: Ubuntu Studio
---

### Post by jim_osborn on 2015-01-27
Since switching from Unity to Ubuntu Studio/Xfce4 the screen on my laptop insists on going dark after ten minutes of inactivity, even though the power cord is plugged in, and the battery-status indicator acknowledges its state. Under Unity, the screen would never go dark unless I explicitly blanked it via <F2>. Here's a list of what I've tried:
removed gnome-screensaver
in Xfce4 Settings Manager:
Screensaver: turn OFF XScreenSaver daemon; set Mode: Disable Screen Saver
Power Manager: General: monitor power management control: yes; show notifications about battery state: yes
On AC: Actions: when laptop lid is closed: Suspend; Put the computer to sleep when inactive for: never; Spin down hard disks: no
On AC: Monitor: Put display to sleep when computer is inactive for (wciif): 0
On Battery: put computer to sleep; Put display to sleep; Switch off display wciif: All Never
unchecked the existing Startup Application Xfce Power Manager
added a new application Xfce Power Manager (new) with --no-daemon as an arg to xfce4-power-manager
reboot
wait ten minutes.. and it still fails

I can't think of anything else to try.

---

### Post by coldraven on 2015-01-27
IIRC Xubuntu has a utility in Settings called Lightlocker. Turn it off!
I'm guessing that this may apply to the UStudio distribution as well.

---

### Post by jim_osborn on 2015-01-27
When I click on the Lightlocker link in the Settings box something flashes onto the screen for a few microseconds, then disappears. I'm guessing the fact that I removed the gnome-screensaver package has something to do with that behavior. Does a screensaver have to actually be present in order to turn it off? Is there something else that can blank the screen beyond what I've tried?

---

### Post by Dennis N on 2015-01-27
The 10 minute screen blanking is probably caused by the DPMS system (Display Power Management System).

[http://www.computerhope.com/jargon/d/dpms.htm](http://www.computerhope.com/jargon/d/dpms.htm)

My experience (so far) is that the newest version of xfce4-power-manager will prevent this:  you need xfce4-power-manager version 1.4.1 or later which are used in Xubuntu 14.10 and 15.04.

If you are still using a 14.04 release, this post has a solution:

[http://ubuntuforums.org/showthread.php?t=2253791&p=13172640#post13172640](http://ubuntuforums.org/showthread.php?t=2253791&p=13172640#post13172640)

Another case of same problem:

[http://ubuntuforums.org/showthread.php?t=2256459](http://ubuntuforums.org/showthread.php?t=2256459)

---

### Post by jim_osborn on 2015-01-27
Dennis N pointed me where I needed to go, so I'm marking this problem solved. It really was a case of the screen blanking for want of sufficient Screensaver. To summarize, I'm running 14.04.1, so I need the xscreensaver daemon to be running, so its existence will distract the DPMS in xfce4-power-manager so that it won't blank the screen after ten minutes of inactivity. After restarting the daemon, I could access the xscreensaver settings, where I left the Mode set to Disable. Then I went to
 Settings->Session and Startup->Application Autostart->Screensaver
making sure its command was: xscreensaver -no-splash, and checked its box so that it would start after a reboot. I rebooted, waited ten minutes, then more minutes, and now do hereby declare the problem solved.  Thanks, guys!

---

### Post by Dennis N on 2015-01-28
Hey Jim, 
Thanks for the feedback. I'm glad to hear this solved the problem for you! I have used the same solution quite a few times.

---

