---
title: "UPS Power Failure Recovery"
date: 2008-02-05
forum: Server Platforms
---

### Post by notaloafer on 2008-02-05
After my first failure to shut down with my server when we had our first power outage yesterday I've decided to take a look on how to better configure my UPS =) .

Right now I have to so when a power loss is detected my APC UPS notifies my server that power has been lost. The server waits 7 minutes for power to return and if it doesn't, initiates a full shut down.

My question is how do I get my server to shutdown fully to the point where when power is returned it automatically reboots? Since it is fully shutting down right now when power returns it doesn't automatically restart.

Can someone tell me the different ways of shutting linux down so I can have the daemon UPS management process (APCUPSD) shut it down enough to the point where the process is still running and can tell the server to start back up again when power is returned? Is there another way to do this?

It's occured to me that ubuntu has several different ways of shutting down; not as cut and dry as "Shut Down" in Windows XP is =P . If you can give me a brief overview on how "halt" works and the different options that would be awesome.

Thanks
-Eric

---

### Post by SergeiFranco on 2008-02-05
you could either turn on resume on power failure in BIOS or on mainboard itself depending on the mainboard (if it is older it should have a jumper, if it is newer it would have option in bios).

---

### Post by notaloafer on 2008-02-05
> **SergeiFranco said:**
> you could either turn on resume on power failure in BIOS or on mainboard itself depending on the mainboard (if it is older it should have a jumper, if it is newer it would have option in bios).

I forgot to mention this in my first post but my BIOS is already set to resume power failure. It's not a power failure that's occuring though. Before the power fails Ubuntu shuts itself down so the BIOS thinks it was just a regular shutdown instead of a power loss.

---

### Post by tgalati4 on 2008-02-05
Apcupsd can also shut down the UPS after a successful shutdown.  If the UPS is shut down, then your server won't reboot.  Make sure you have it configured to leave the UPS powered after system shutdown.  Realize that your UPS can take a hit when the power returns because of the power spike, so sometimes it's better to have apcupsd power down the UPS to save the circuitry from wonky power when power is finally restored.

What caused the original shutdown failure?

---

### Post by Cato2 on 2008-02-10
See [https://help.ubuntu.com/community/apcupsd](https://help.ubuntu.com/community/apcupsd) - this points out an edit you can make to the 'halt' script in /etc/init.d that removes the '-p' option - the effect should be that Ubuntu doesn't actually power off the system when apcupsd shuts down.

If this doesn't do what you want, you could try writing a script as at [http://ubuntuforums.org/showpost.php?p=4302102&postcount=37](http://ubuntuforums.org/showpost.php?p=4302102&postcount=37) - only instead of hibernating, make the script do what you need.  As long as you can find a Linux command that will leave your system in the right state to power up when utility power is resumed, you should be able to make this work.

---

