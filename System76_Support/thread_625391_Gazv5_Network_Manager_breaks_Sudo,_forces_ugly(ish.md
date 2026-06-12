---
title: "Gazv5 Network Manager breaks Sudo, forces ugly(ish) restart"
date: 2007-11-27
forum: System76 Support
---

### Post by DBO on 2007-11-27
I am loving my new laptop, but I do have one tiny problem with it.  Whenever I put it somewhere that it cant get a wireless signal for long enough, it fails to recover... at all really.  The network manager seems to lock down sudo in some way (when running sudo on a tty it does not even ask for my password) and most applications will not launch properly.  Gnome-terminal is one of those handy things that doesn't launch.  Also the shutdown/restart buttons fail to work at this point.

Any help would be appreciated.

Jason

---

### Post by DBO on 2007-11-28
Here are the relevant bits of the syslog

---

### Post by osx424242 on 2007-11-28
I've had the same problem on my panv3, occasionally.  It happens after I lose my wireless connection, which seems to happen after doing some heavy networking (spending some time on a remote desktop to another computer on my household network, or once 2/3 through downloading an Ubuntu ISO).

I can't log out or restart (pressing any of the 3 buttons -- top right 'power' button on the upper menu bar; System | Quit...; tapping the power button on my case) does nothing.  I usually am unable to launch new applications, although I can open a new tab if I already have a terminal open.  'sudo reboot' just hangs without asking for a password, like the OP's 'sudo' issue.

ctrl-alt-f1 (or f2; assuming also f3-f6 but haven't tried) lets me log in to a CLI but 'sudo reboot' still hangs.  I forget what ctrl-alt-f7 at this point does, it either returns to my graphical session or doesn't :).

I believe that once or twice the system may have recovered after I walked away from it and waited a long time, but I'm not really positive.  I'm fairly sure that I've walked away and waited a long time and the system has _not_ recovered, in which case the 'solution' has just been to hold down the power button until my laptop shuts down.

I've been hoping to get more information to help with replication, but it hasn't happened yet; since you posted I thought I'd add my experiences.

Running 7.10, used update manager to get here from 7.04 (no cd-rom, but have a few Fx tabs open, still trying to learn enough to look for a solution), Intel 3495abg wireless card with a linksys wrt54gs router, WAP encryption.

---

### Post by DBO on 2007-11-28
I have found that this seems to be somehow related to having large wireless networks with multiple access points.  If you look in my log you will see the problem seems to arise when it switches from one AP to another.  Anyhow any feedback on possible fixes for this one would be fantastic.  Until then I just put the darn thing to sleep when Im not using it and that seems to take care of the issue.

---

### Post by thomasaaron on 2007-11-28
Yeah, I don't think it is specific to the GazV5. It is more likely a bug with Network Manager. I have the same thing happen occasionally on my DarU1.

Probably the best workaround is to disable wireless networking via the Network Manage applet if you don't need it.

---

