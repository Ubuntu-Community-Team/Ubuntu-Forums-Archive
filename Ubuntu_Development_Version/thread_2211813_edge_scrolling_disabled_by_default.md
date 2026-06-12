---
title: "edge scrolling disabled by default"
date: 2014-03-17
forum: Ubuntu Development Version
---

### Post by monkeybrain20122 on 2014-03-17
The default is set to two finger scrolling but this never works on all the laptops I have installed Ubuntu on. But edge scrolling, which always works is disabled. I think this is a very strange default inherited from gnome shell and should be changed else new users would think Ubuntu doesn't work on touchpad. 

To change this behaviour go to System settings > Mouse and Touchpad and uncheck two finger scrolling.

---

### Post by mc4man on 2014-03-17
It was inherited by 'on purpose' so to speak. Seems to be a matter of presumed fact,  being that most people now expect 2 finger scroll
(vs. some people expecting edge
In regards to hardware that doesn't support 2 finger  paragraph 3 summed up in tracking bug, probably true though some did object to...
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1217166](https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1217166)

In any event the default is 99.9999% not to be changed
This did occur in 13.10 & initially for unsupported touchpads switching back to edge could only be done in dconf, no idea if that is still true as don't have such hardware here (assuming it was fixed
ref. here - [https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1233055](https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1233055)

---

### Post by monkeybrain20122 on 2014-03-17
My hardware is only 3-4 years old and I can enable two finger scrolling with a script (so the hardware does support it). but the dconf settings never work. Unchecking two finger scrolling in System Settings appears to restore edge scrolling.

---

### Post by monkeybrain20122 on 2014-03-24
Many touchpads actually support both edge and two finger scrolling. Why is it that ubuntu (actually gnome) only alows you to choose one??? Is it so hard to support both options being enabled? To enable both I make a script and set it to autostart.

```
#!/bin/bash

synclient VertEdgeScroll=1
synclient VertTwoFingerScroll=1
```

---

