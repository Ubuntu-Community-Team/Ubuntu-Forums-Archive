---
title: "Refresh Rate Issue (NVidia)"
date: 2009-02-14
forum: System76 Support
---

### Post by chez17 on 2009-02-14
S I have an NVidia card in my laptop (Pangolin Panp4n, Intrepid 64 bit) and the refresh rate isn't synching with the system. If I goto my NVidia control panel, it says the refresh rate is on "Auto". Now when I goto to screen resolution in preferences, it says I have the choice of 50 or 51 hz. If I goto my NVidia control panel and set the refresh rate from auto to 60 hz, the only options I have now in my screen resolution preferences are 50, 51, and 78 hz. Shouldn't the two be consistent? How do I get them to match up? Compiz is a just a tad choppy and I would be this has something to do with it. Any thoughts?

---

### Post by ctsdownloads on 2009-02-15
> **chez17 said:**
> S I have an NVidia card in my laptop (Pangolin Panp4n, Intrepid 64 bit) and the refresh rate isn't synching with the system. If I goto my NVidia control panel, it says the refresh rate is on "Auto". Now when I goto to screen resolution in preferences, it says I have the choice of 50 or 51 hz. If I goto my NVidia control panel and set the refresh rate from auto to 60 hz, the only options I have now in my screen resolution preferences are 50, 51, and 78 hz. Shouldn't the two be consistent? How do I get them to match up? Compiz is a just a tad choppy and I would be this has something to do with it. Any thoughts?

I have a NVIDIA card running dual monitors on my desktop PC. This being said, I have never, ever bothered with the GNOME resolution preferences as I take care of this exclusively in nvidia-settings. 

Long story short, I have never bothered to compare resolution between the two apps. So I guess the question is are you having resolution or visible refresh rate issues?

---

### Post by thomasaaron on 2009-02-16
Is the image on your external monitor choppy? If so, this really has nothing to do with nVidia (I think). It's more likely that, if you, have a cheap monitor, Ubuntu isn't detecting it correctly, or is only making a guess at it. In these situations, it's often necessary to manually configure the monitor in xorg.conf.

---

