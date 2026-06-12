---
title: "midi controllers and ubuntu 8.04"
date: 2008-06-03
forum: Ubuntu Studio
---

### Post by tbozot on 2008-06-03
I have a edirol pcr-30 (usb).

I seem to be having a problem just getting the edirol to play. I've used "jack" "rosegarden" "qsynth" and the latest zynaddfx. Rosegarden sees the edirol as a pcr -20. None seem to let the edirol "join in the fun!"

any suggestions?

---

### Post by Stochastic on 2008-06-03
Does jack see it in its midi tab?  I've got access to the same model (not right now though) so I'll attempt to get a signal myself and report back.

---

### Post by tbozot on 2008-06-03
thanks for the reply,

although the controller I have is a pcr 30, jack reads it as pcr 20; which is okay as long as I can punch the keys and get some sounds. At this point I dont receive any sounds from the pcr 30.

---

### Post by prismatic7 on 2008-06-03
> **tbozot said:**
> thanks for the reply,

although the controller I have is a pcr 30, jack reads it as pcr 20; which is okay as long as I can punch the keys and get some sounds. At this point I dont receive any sounds from the pcr 30.

try installing kmidimon (in the repos) - it's a really useful tool for midi debugging. That will tell you straight away if the device is sending midi messages correctly.

---

### Post by tbozot on 2008-06-03
thanks for the info.

looks like kmidimon picks up the keyboard just fine. No sound though.

there has to be a setting somewhere that pushes my pcr 30 through. I tried a number of programs and found that "jack" picks it up in name only. Kmidimon picks it up in name and shows (on screen) the movement of the keys.

---

