---
title: "No sound on Meerkat Ion Nettop in Natty"
date: 2011-05-03
forum: System76 Support
---

### Post by Rob_H on 2011-05-03
Fresh install of Natty on a Meerkat Ion Nettop. I've got audio hooked up to optical S/PDIF as well as HDMI, but I'm not getting sound from either one. I've tried different sound profiles in Unity to no avail. Anyone else running into this? (Possibly related: The System76 driver UI does not start either. Says the system is unsupported.)

---

### Post by isantop on 2011-05-05
What do you have selected in the Output and Hardware Tabs of the sound preferences window? Also, do you have the Nvidia Proprietary Driver installed?

---

### Post by Rob_H on 2011-05-05
> **isantop said:**
> What do you have selected in the Output and Hardware Tabs of the sound preferences window? Also, do you have the Nvidia Proprietary Driver installed?

I tried every choice there. The NVIDIA driver was installed and working fine for video (verified through *glxinfo*), even though the *Additional Drivers* tool reported that the driver was enabled but not currently in use.

In the end, I got frustrated and went back to Kubuntu. Sound is working fine there through the S/PDIF output. Thanks anyway.

---

