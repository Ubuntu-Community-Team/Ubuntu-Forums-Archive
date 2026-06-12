---
title: "[SOLVED] Problems (and solutions) encountered during Vista installation"
date: 2008-03-26
forum: Windows
---

### Post by twin_57103 on 2008-03-26
I just built a new system and installed Vista for the first time.  I discovered a couple quirks that initially looked like hardware problems but were really installer issues.  I though I'd post it here in case it is useful to someone else.

[B]This applies to clean installs with multiple hard drives or more than 3 Gb RAM.
[/B]

**RAM**: The Vista installer does not do well when more than 3 Gb of RAM is present.  You may get blue-screen errors: 
IRQL_NOT_LESS_OR_EQUAL
STOP 0x0000000A

I had to remove one of my 2 Gb chips to reduce the RAM from 4 Gb to 2 Gb.  You can put it back once you finish installation.


**Multiple hard drives**: I believe this applies only to SATA drives that have not been previously formatted
Messages:
"This computer's hardware may not support booting to this disk"
OR
"Windows cannot find a system volume that meets requirements for installation."

The Vista installer can't distinguish between the drives and gives errors about the drives not being supported. In order to correct this, you have to create partitions, then restart the computer before you are able to proceed with installation.
Note: exiting out of the installer and beginning again is not enough.  You have to give it the 3-finger salute (ctrl-alt-del) or power down and back on.
[Microsoft article]("http://support.microsoft.com/kb/925481")

---

### Post by iSplicer on 2008-03-26
Thanks, for the tip, that has to be one of the most retarded errors i have ever seen in Windowsdom

---

### Post by twin_57103 on 2008-03-29
A followup...apparently there are considerable sleep/resume issues with Vista.  I am having trouble with resumes under Vista.  I updated the mouse driver, which was suggested in a Microsoft article, but I am still having trouble.  When I wiggle the mouse and/or press keyboard keys, the fans turn on, but the monitor never resumes.  I have to do a hard shut-down and reboot.  I may end up disabling sleep/resume and have to fully shut down the computer for the meantime - I'd rather not scramble my hard drives with all these hard shutdowns.

I'm not asking for tech support here (although I'd appreciate any ideas).  I'm just trying to point out a few details in case they are helpful for others.

---

### Post by Joeb454 on 2008-03-29
It could be the Graphics Card. I'm sure the monitor is fine, but if the Graphics card isn't sending a signal to the monitor...then clearly the monitor will do nothing ;)

---

### Post by twin_57103 on 2008-03-29
That could be. I'll look into updates for the driver once I get back to Windows (I installed the driver from the CD, but haven't looked into any web updates).  I'm working on finally dual-booting - I had to use 8.04 beta because the stable versions seemed completely incompatible with my hardware (go figure).

---

