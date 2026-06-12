---
title: "Sound over HDMI on Nexus 7"
date: 2016-05-11
forum: Ubuntu Phone and Tablet
---

### Post by andoru on 2016-05-11
I can't get any sound output over HDMI on my Nexus 7 (2013). 

First, I tried with Ubuntu Touch booting using Multirom. The display output was fine, but no sound. 

Then, I did a proper installation using ubuntu-device-flash. Again, the display output was fine, but no sound.

(In both instances, the sound comes out of the tablet speakers.)

In Android, the sound comes through just fine. So I don't think it's an issue with the cable or the slimport adapter.

Any ideas?

---

### Post by lapor2 on 2016-05-13
I have tried it with my M10 and it also doesn't work. I think this is Ubuntu bug and has to be resolved. It's not a hardware problem.
I tried to add a bug, but I don't know on which project in launchpad I should refer.

---

### Post by andoru on 2016-05-13
I imagine it's the system image since it's not specific to one of the apps.

[https://launchpad.net/canonical-devices-system-image](https://launchpad.net/canonical-devices-system-image)

---

### Post by dtarrant on 2016-08-04
> **lapor2 said:**
> I have tried it with my M10 and it also doesn't work. I think this is Ubuntu bug and has to be resolved. It's not a hardware problem.
I tried to add a bug, but I don't know on which project in launchpad I should refer.

Same problem here. Sound outputs from M10 speakers, but not over HDMI cable.

---

### Post by lapor2 on 2016-08-05
Anybody reported a bug?

---

### Post by dtarrant on 2016-08-05
Not me. Not sure how to do this.

---

### Post by lapor2 on 2016-08-05
Here you go: [https://bugs.launchpad.net/canonical-devices-system-image/+bug/1576037](https://bugs.launchpad.net/canonical-devices-system-image/+bug/1576037)
Otherwise, go to the lauchpad and try to find the package it is concerning (Mir, Unity8,...) and report the bug. You will have to sign in, but it is the same Ubuntu One account that you are using here :)

Cheers

---

