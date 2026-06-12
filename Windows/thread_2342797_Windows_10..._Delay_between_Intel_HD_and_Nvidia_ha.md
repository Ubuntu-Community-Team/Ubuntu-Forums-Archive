---
title: "Windows 10... Delay between Intel HD and Nvidia handoff optimus..."
date: 2016-11-10
forum: Windows
---

### Post by arlenn2 on 2016-11-10
I have been picking up 3D CAD for some projects and have noticed an odd behavior; curious if anybody else has seen this and may know a resolution?

There seems to be a significant lag in the handoff from the Intel HD and the GT750m GPU.  to the point when rotating a part, there is what feels like 250-500ms from input to reaction; after moving an on the Nvidia GPU everything actually moves pretty smoothly.  What it translates to is a really frustrating CAD session.

I initially thought it the 750m might just be utter crap (it still might be) but in exploring it with the Afterburner Overclock tool, I can see that the system tries to hold on the Intel GPU longer than necessary.  I do have the Nvidia settings set to prefer the Nvidia GPU, but it still tried to use the Intel GPU maybe more than it should....  (long pre-amble)

is there a way to force the GPU totally to the Nvidia?  Is there a way to move the threshold down to it tips into the Nvidia a bit sooner?

Thanks in advance.

---

### Post by arlenn2 on 2016-11-10
Disaster averted... It seemed to be a setting.  Setting the global perferred GPU to Nvidia seemed to make the difference, as well as turning everything to performance.

---

