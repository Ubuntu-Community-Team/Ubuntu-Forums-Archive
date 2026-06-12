---
title: "Daru2 wireless getting killed with System76 driver restore"
date: 2009-01-03
forum: System76 Support
---

### Post by dtrask on 2009-01-03
Last night I bought and installed a new Linksys WRT160n wireless router.  All my other laptops work including Ubuntu based ones, except my Daru2.  I decided to wipe my machine to try and resolve the issue.  If I do a simple install with no addition of System76 drivers, my wireless works.  The moment I add the drivers either by "restore" or "install drivers" the wireless (or should I say NetworkManager) stops detecting my access point.  I can enter it manually, but after a while it stops working.  However, it does work if I simply don't add the drivers.  I'd like to have the rest of it though.  Any ideas?

Oh...and I had run all the recent Ubuntu Intrepid updates last night when it b0rked.  Not sure if it's the router or a simple coincidence.  I have other Hardy based laptops that are running fine.

PS...the access point is running with no security...so it's not that

---

### Post by thomasaaron on 2009-01-05
That's interesting because the System76 Driver actually does not do anything to the wireless card. The wireless card in the DarU2 works out of the box with Ubuntu, and we add no modifications for it.

Are you running proposed updates? If so, it's possible that the latest proposed kernel is causing the problem. If you're running with the proposed kernel, can you try running a previous one?

---

