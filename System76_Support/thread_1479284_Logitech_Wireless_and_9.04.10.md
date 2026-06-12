---
title: "Logitech Wireless and 9.04/.10"
date: 2010-05-10
forum: System76 Support
---

### Post by BuggyFunBunny on 2010-05-10
I have the MX-610 running with 8.10, and I suppose I should upgrade.  I ran the 9.04 LiveCD to test, and while I get X, neither the Keyboard (das Keyboard) nor the mouse work.  I understand that the config file has been replaced, but I'm leery about running the network Upgrade from Synaptic, and ending up with a machine I can't use.  I need to be able to get to the 'net to run my stock's account without interruption.

Any thoughts?  

I have PS2 keyboard and trackball someplace; I haven't attempted to use them.  In any case, both the das and MX-610 are not new devices; that they aren't recognized by the liveCD is not a Good Thing.

---

### Post by isantop on 2010-05-10
Try a 10.04 LiveCD. It may have better support for your hardware.

---

### Post by BuggyFunBunny on 2010-05-11
> **isantop said:**
> Try a 10.04 LiveCD. It may have better support for your hardware.

I've seen too many issues with 10.04 and other software, not in the Repository.  Most of what I have isn't.  

A clarification on what "fresh install" means, and what need be backed up.  I infer from some messages that only the root partition is replaced, /home (and any other partitions, I suppose) don't get overwritten.  

If that's so, then I can go to 9.04 as fresh.  

But what about the config change??  Where is this documented?

---

### Post by isantop on 2010-05-11
The Xorg.conf configuration? That actually got removed in 9.04 in favor of using HAL to auto-detect your optimal settings. Changes made to configuration are done through HAL files.

Unless you want to try 9.10, which has a lot of the HAL removed. It works great, but like I said, no HAL, and you may want that.

The other option is to write a config file yourself, from scratch. That can be some work, but there are some tools out there that can help you do it.

---

