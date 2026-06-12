---
title: "Touchpad sensitivity on GAZv5"
date: 2009-02-09
forum: System76 Support
---

### Post by Tart on 2009-02-09
Hi All,

I have GAZv5 with 8.04 on it. My wife complains that touchpad is little bit too sensitive for her. Whenever she types, mouse cursor jumps around often when she touches touchpad accidentally.

What is the best way to adjust sensitivity on the touch pad? 

There is a Touchpad configuration program available in Add/Remove programs. But it gives the following message

```

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics
```

before I modify xorg.conf file, would that be a best way to deal with touchpad sensitivity?  Am I on the right track? Where in xorg.conf should I insert SHMConfig (Input device section probably)? 

Thank you for your help!

---

### Post by thomasaaron on 2009-02-10
I get the same complaint from my wife!

Don't use gsynaptics. It is for Synaptics touchpads. Your GazV5 has an ElanTech touchpad, which is not compatible with gsynaptics.

A while back, some developers were working on a more configurable driver for the ElanTech, but I think that sort of petered out.

The only adjustments for it are the ones in System > Preferences > Mouse. You should be able to adjust the sensitivity and/or double-click timeout somewhat.

---

### Post by Tart on 2009-02-10
Thanks for your reply Thomas.

I thought that System > Preferences > Mouse - controls mouse.

If I have USB mouse hooked up this option will adjust sensitivity for both mouse and touchpad?

I'll experiment with it once I get home.

---

### Post by thomasaaron on 2009-02-10
It definitely adjusts the touchpad if you're only using the touchpad. Not sure what the effect is if a USB mouse is attached too.

---

