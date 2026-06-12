---
title: "Can't grab keyboard or mouse diagnostic"
date: 2006-01-09
forum: Server Platforms
---

### Post by UphillSkier on 2006-01-09
Hello

Yesterday I returned to my Breezy box after leaving it up and on the network for a while.  When I used the keyboard and mouse I got diagnostic windows popping up from gnome to the effect that "Cannot grab keyboard" or "Cannot grab mouse" and warning me that malicious software might be monitoring by keystrokes.  I logged out and shut down the system.

Tonight when I powered up I get no similar diagnostics but I am afraid that something nasty may have happened.  I don't even want to risk logging in as root or sudo'ing for fear of eavesdropping.  What should I do short of wiping the system partition and reinstalling?

thanks for any help
Andy

---

### Post by stuporglue on 2006-01-09
If you boot from a live CD you can mount the partition with noexec. Then you can check it out from a clean system (the live CD) and knowing that nothing can run from that disk (noexec). 


If you think you've been hacked though the only way to know _for_sure_ that it's clean is to wipe it.

---

### Post by Jasper84 on 2006-11-13
I get that same error message sometimes. I feld a bit unconfortable with it but still use it and the password anyway. There is not really anything too private on the computer.
But i still would like to make sure, and the mounting from a liveCD part makes sense, but what do you do after that, I mean how to find tampering of the system? Anything i can do before I get hacked to see if it is tampered with? (vaguely heard of tripwire, guess i should do some reading myself when i get time)

---

### Post by ahaslam on 2007-10-27
I got this message today, "could not grab mouse... a malicious client may be eavesdropping". I'm running Gutsy and it was only really ok for a couple of days. Since then I've had problems booting, running app's, logging out, general stability & now this. I've checked for root kits finding nothing, aparmor shows no complaints & I'm currently checking for viruses.

PS, I've had to ditch gnome in favour of openbox, as it became completely unresponsive, doubt it can be fixed. It looks as though I've been compromised in some way, I just wish I could learn from it...

---

### Post by ahaslam on 2007-10-27
Well clamscan only came up with some oversize .zips and a phishing email on another partition. I guess it's clean, just screwed up some other way...

---

