---
title: "Can't turn off laptop after doing fresh install"
date: 2011-05-30
forum: System76 Support
---

### Post by flucoe on 2011-05-30
Hi,

I couple of weeks ago I decided to upgrade from Ubuntu 10.04 to 11.04. I wanted to do a fresh install so I downloaded the iso, I checked it, then I burned the CD and I also checked it for any defect. In both cases the outcome was that the image and the CD were OK.

I did a fresh install following the instructions from [here]("http://knowledge76.com/index.php/Restoring_Your_System") and up to the point when I had to restart the laptop (a PanP7) everything worked perfect. However, when I pressed the "restart now" button the screen changed to the normal black screen with white letters and never changed again so I had to "manually" turn off the computer. After this, the same happened more than half of the times I turned off the laptop during the following days, but not always. After a day or two I decided to go back to 10.04 because obviously this was not something I wanted to happen. Back to 10.04 this has never happened again (and it never happened before upgrading).

Just my problem or somebody else had the same problem? If the .iso and the CD didn't report any problem, what might have happened? I did not burn another CD because I just didn't have enough time, but could it be that even though there was no error reported, either the CD or the iso were damaged? Any idea how to know this if the "tests" didn't report anything weird? By test I mean md5sum and "check CD for defects" or something like that that appears when you use the Live CD.

Thanks,

Fernando

---

### Post by scarey9 on 2011-06-02
+1 on this one. Most of the time i am not able to shutdown or restart my computer. It hangs on in the terminal screen. I let it sit for 45 mins once b4 finally poking it in the eye. Sometimes it works, most times it does not.

---

### Post by isantop on 2011-06-03
What do you get if you run this command from a terminal:

```
sudo reboot
```

---

### Post by flucoe on 2011-06-05
> **isantop said:**
> What do you get if you run this command from a terminal:

```
sudo reboot
```

Well, nothing...it just reboots the system, but I'm back using 10.04 with no problems, so I'm not sure why running this should say anything related to what happened when I upgraded to 11.04. Is there something I'm missing?

---

### Post by isantop on 2011-06-06
It would have to be run from 11.04.

It sounds like the CD was physically damaged. It is possible, though unlikely, that a damaged CD will return an error. Would it be possible to try it from another CD, just to rule that out as a possibility?

---

