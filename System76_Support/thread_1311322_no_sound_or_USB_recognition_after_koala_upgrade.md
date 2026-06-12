---
title: "no sound or USB recognition after koala upgrade"
date: 2009-11-02
forum: System76 Support
---

### Post by plasmid203 on 2009-11-02
I have a System76 Darter notebook that I just upgraded to koala.  There is no sound and it won't recognize any USB flash drives.  I installed the new system76 driver repository and "restored" as directed on some other threads, but still no luck.

HELP!

---

### Post by petmadcon on 2009-11-02
There is no sound and it won't recognize any USB flash drives.

---

### Post by xakh on 2009-11-02
Well, you can type 
```
sudo alsa force-reload

```
to get your sound back, but it only works until you reboot. I'm having the same problem with USB drives, and the memory stick slot though.

---

### Post by ctsdownloads on 2009-11-02
> **petmadcon said:**
> There is no sound and it won't recognize any USB flash drives.

Tested five different Sandisk flash drives on 9.10 - all work fine for me.
As for audio, I have never had a problem. But you may want to double check your advanced volume control...while making sure you are working with no USB sound devices connected for testing.

On the volume control, right click it and select Sound Preferences.

Then check the output volume, under hardware tab make sure only the Internal Audio is shown, under Applications tab you want to open audio apps with it open to make sure sliders are turned up. 

This has been the most common mistake for most upgraders. :)

Also, run those updates! ;)

---

