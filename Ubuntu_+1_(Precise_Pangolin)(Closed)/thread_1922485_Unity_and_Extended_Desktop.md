---
title: "Unity and Extended Desktop"
date: 2012-02-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by saneearth on 2012-02-08
Using multiple monitors with Unity 12.04, nVidia, and latest updates. Both of my monitors now have the Unity panel, when in 11.10 with the same settings the panel appeared only in the primary monitor as it is supposed to. Though the appearance would not be so bad, running the mouse pointer across or dragging something from one screen to the next is like running across a "speed bump". The mouse pointer hesitates or gets hung at the panel on the extended desktop panel. Is the panel on the extended desktop now by design? Also, I still get the "speed bump" even when I hide the panels which I do typically.

---

### Post by kaldor on 2012-02-08
This is entirely by design

Basically, the launcher was too prone to false positives in 11.10. For example, if you maximized Firefox and reached for the back button you would very often and commonly trigger the launcher. On 11.10, I launched programs every time I clicked something on the left side of a maximized window.

The solution (which I currently hate with a passion because it's annoying and unnatural) is to apply "pressure" to the edge to trigger the launcher. The same idea has been applied to the monitor; after a certain threshold the cursor should push itself through to the next screen.

This UI decision really needs to be looked into. Even just giving us the option of placing the launcher on the bottom would solve this issue entirely.

---

### Post by grahammechanical on 2012-02-08
Have you seen the extra adjustments that can now be made in CCSM? The Experimental tab of the Ubuntu Unity Plugin has a setting called Launcher Edge Stop Overcome Pressure. The tool tip says this: "Amount of mouse pressure required to push into the next monitor."

Regards.

---

### Post by kaldor on 2012-02-08
> **grahammechanical said:**
> Have you seen the extra adjustments that can now be made in CCSM? The Experimental tab of the Ubuntu Unity Plugin has a setting called Launcher Edge Stop Overcome Pressure. The tool tip says this: "Amount of mouse pressure required to push into the next monitor."

Regards.

It's in the "Behaviour" tab in the appearance section now too. Still, it feels unnatural.

---

### Post by saneearth on 2012-02-09
> **grahammechanical said:**
> Have you seen the extra adjustments that can now be made in CCSM? The Experimental tab of the Ubuntu Unity Plugin has a setting called Launcher Edge Stop Overcome Pressure. The tool tip says this: "Amount of mouse pressure required to push into the next monitor."

Regards.

I am a little afraid of CCSM. Have had multiple experiences where a fix was in order afterwards. I'll likely have a look though with I have time to make changes.

---

### Post by saneearth on 2012-02-09
I guess my main issue though is that there is an in my opinion un-needed panel on my secondary monitor that was never there before. I will take a look at CCSM and some other things, but by design I do not think a panel should show up on an extended desktop. I can think of no other time I have seen this behavior repeated in any OS unless you are mirroring the desktop, then of course you would have it.

---

### Post by cariboo on 2012-02-09
Multiple monitor support is still a work in progress, If you still have the problem of having a second launcher around the end of March, then is when I'd start worrying.

---

### Post by saneearth on 2012-02-09
> **cariboo907 said:**
> Multiple monitor support is still a work in progress, If you still have the problem of having a second launcher around the end of March, then is when I'd start worrying.

I kind of figured as much. I was really just making a comment to see if was just me or others also and if this might not be something "new". Everything for the most part seems pretty stable.

---

### Post by dazza5000 on 2012-02-17
I would also like to be able to have the option to have the launcher on only one monitor. I have 4 monitors lined up horizontally and having a unity launcher on each screen could be seen by some as being wasteful :) thank you Ubuntu! Canonical and Unity rock!

---

