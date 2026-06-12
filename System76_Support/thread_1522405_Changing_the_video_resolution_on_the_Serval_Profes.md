---
title: "Changing the video resolution on the Serval Professional"
date: 2010-07-02
forum: System76 Support
---

### Post by volkerbradley on 2010-07-02
Occasionally, I need to change the resolution of the screen.
Presently, the NVIDIA X Server reports 1900x1080 Auto
I have clicked on System -> Administration -> NVIDIA X Server settings but do not know how to use this application.
How do I change the resolution using the NVIDIA X Server Settings application?

---

### Post by isantop on 2010-07-02
Once the app is opened, you can click X Server Display Configuration to change the resolution. Be sure to click "Save to X Configuration File" if you want your changes to be retained when you reboot.

The first time you use "Save to X Configuration File", you may get an error reading "Failed to parse existing /etc/X11/xorg.conf file" or something very similar. This is normal. Just click okay and you should be okay.

---

### Post by volkerbradley on 2010-07-03
For some reason I had failed to see Resolution category in this app.  Found it.
Thank you.

---

