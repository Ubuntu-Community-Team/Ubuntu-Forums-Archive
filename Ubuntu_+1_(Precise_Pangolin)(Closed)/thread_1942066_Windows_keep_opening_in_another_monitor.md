---
title: "Windows keep opening in another monitor"
date: 2012-03-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by cuby on 2012-03-16
I have 1 monitor and an LCD TV arranged in as a dual monitor setup with an nvidia card.
Ubuntu's display preferences doesn’t recognise the monitors, so I have to use Nvidia settings.

The system works but with unity 3d windows keep poping in the monitor I'm not using. It's silly. Because I only turn on the TV when I want to see video, I can't use the system unless I have the other monitor on.

Because this is impractical I switched to Unity 2D were this behaviour doesn't happen. 

Can someone help me configure Unity 3D to open windows in the right monitor?

---

### Post by skewty on 2012-03-17
Please submit a bug report.  I am having a similar problem and will mark your bug as affecting me as well.

---

### Post by pqwoerituytrueiwoq on 2012-03-17
i would guess yuo need to change the default monitor no idea how that works on unity...

---

### Post by cuby on 2012-03-17
pqwoerituytrueiwoq, I've done that (in nvivia settings) and Unity 3D ignores it.

---

### Post by cuby on 2012-03-17
I filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/957786](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/957786)

---

### Post by pqwoerituytrueiwoq on 2012-03-17
i know from experience nvidia setting can be a bit finicky about the primary monitor setting i tend to have to apply it 2 twice

---

### Post by cuby on 2012-03-18
It's a problem in the NVidia driver implementation. 
Check the 3rd comment:

[https://bugs.launchpad.net/bugs/957786](https://bugs.launchpad.net/bugs/957786)

---

