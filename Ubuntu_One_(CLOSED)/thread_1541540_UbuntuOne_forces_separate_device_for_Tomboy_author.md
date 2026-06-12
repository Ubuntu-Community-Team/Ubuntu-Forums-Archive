---
title: "UbuntuOne forces separate device for Tomboy authorization"
date: 2010-07-29
forum: Ubuntu One (CLOSED)
---

### Post by david.rahrer on 2010-07-29
Before I submit a bug, I wanted to see if anyone can tell me why this happens.  When I first start using UO, it requested that I add my computer to my UO account.  I entered the name of my machine, ie. "desktop-name".  Once I did that, the music store worked properly, and I was able to use the Evolution Contacts sync and regular files in the ~/UbuntuOne folder.  These all showed up in my web interface.

Now, when I set up Tomboy to sync with UO (Tomboy Web), it sends me to the Confirm Computer Access page again, asking me to put in my device name again.  So I enter again "desktop-name" and it logs in and Tomboy syncs.  The problem is that two devices now show up under Machines, and also under System > Preferences > UbuntuOne > Devices.  I've tried deleting both devices, and starting from scratch as described [here]("https://bugs.launchpad.net/ubuntuone-client/+bug/514723/comments/16") but it always does the same thing.  

Is there a reason I must have two devices listed when I'm on the same system?  Has anyone else noticed this?  FWIW, each confirmation request lists a different token, it just seems that once I have authorized my system, that all the sync connections should auth under the same credentials.

Any help is appreciated.

---

### Post by duanedesign on 2010-07-30
Yes Tomboy requires a separate OAuth Token.

---

### Post by david.rahrer on 2010-07-30
> **duanedesign said:**
> Yes Tomboy requires a separate OAuth Token.

Thanks.  At best this seems confusing.  Any idea why it was done this way?

---

