---
title: "Ubuntu/Debian UPS setup?"
date: 2005-11-30
forum: Server Platforms
---

### Post by mwnovak on 2005-11-30
I run a server install of Ubuntu 5.10 on a headless Apple G4 Cube as a personal web and file server.  It's my hobby machine.

I'd like to add a UPS for the machine to protect against abrupt shutdowns in the event of power failure.  Several good articles exist regarding Debian and UPS's (for example, see [http://update.itlab.musc.edu/node/126)](http://update.itlab.musc.edu/node/126)), but I'm trying to ensure that my machine can support a UPS before I actually buy one.

An initial problem was figuring out how to make a Linux G4 Mac restart automatically after a power failure.  For my solution, see: [http://ubuntuforums.org/showthread.php?t=96379](http://ubuntuforums.org/showthread.php?t=96379)

As indicated in that thread, the "server_mode=1" variable of the 2.6.x kernel does the trick.  However, right now, "restart after power failure" only works in the event of an actual power failure (i.e. when I simply pull the plug on the server, however ill-advised).  It does _not_ work following any graceful shutdown command ("shutdown -h now", "halt", or "halt -f"; I _have_ set HALT="halt" in /etc/default/halt).  In the case of graceful shutdown, the machine will not power up after removing and restoring power.

If I'm not mistaken--and I may well be--I need a shutdown command that brings Linux down _without_ actually powering off the machine... this would allows the UPS to ultimately kill power to the box, which should in turn allow the "server_mode=1" variable to bring the machine back up when the UPS restores power.

Am I mistaken?  If so, I'm hoping someone can explain how this all works.  If I'm not mistaken, I'm hoping someone can explain how to shutdown my machine in a way that will allow it to reboot after the UPS restores power.

Thanks in advance for any suggestions,

--MW

---

### Post by amohanty on 2005-12-01
Have you tried:

[http://www.networkupstools.org/](http://www.networkupstools.org/)

I installed from source, but basically if you mobo supports it, you can use a script in their FAQ to make your system come back up after a gracefule shutdown.

HTH
AM

---

### Post by mwnovak on 2005-12-01
[QUOTE=amohanty]Have you tried:

[http://www.networkupstools.org/](http://www.networkupstools.org/)

I installed from source, but basically if you mobo supports it, you can use a script in their FAQ to make your system come back up after a gracefule shutdown.[/QUOTE]

Hmmm...

Also from the FAQ at networkupstools.org:

> 
Q: My PowerMac G4 won't power back up by itself after the UPS shuts
    down.  What can I do about this?

 A: This is about the same situation as the ATX question above, only
    worse.  Earlier Macs apparently supported a hack where you could
    cat some magic characters at /dev/adb to enable "server mode".
    This would instruct the system to reboot while unattended.

**snip**

    Unfortunately, the hardware has evolved and there is no good
    equivalent for this hack on today's systems.

    If you find out how to do this, please send me some mail, since
    this affects one of my systems and my stop-gap solution is getting
    cranky.


I'm going to email the folks at networkupstools.org regarding both the "server_mode=1" flag and their mentioned "stop-gap" solution.  

Either way, it's looking like I've stumbled across a problem without an easy workaround.  I just have a hard time believing that there isn't a single Apple G4 server in the world that runs Linux and plays nicely with a UPS.  

Can someone check me on this: everything will work as desired if I find a shutdown command that halts the system without actually powering it off, right?

--MW

---

### Post by curtistee on 2005-12-03
[QUOTE=mwnovak]I've stumbled across a problem without an easy workaround.  I just have a hard time believing that there isn't a single Apple G4 server in the world that runs Linux and plays nicely with a UPS.  
--MW[/QUOTE]
Not sure if this'll help, but in the Tiger OS release there's a preference which can be set to auto-reboot after a power failure. I don't normally use it, so AFAIK it may have well been available in earlier OSX releases.

Regarding UPS software, I'd heartily recommend APCUPSD ([http://tinyurl.com/dhqk9)](http://tinyurl.com/dhqk9)). I've been using it for years on my Mandrake (soon to become Ubuntu) server with a budget unit (Back-UPS CS500), & it works like a champ. I assume, of course you're running an APC UPS ;-)

Good luck with it; HTH.

---

