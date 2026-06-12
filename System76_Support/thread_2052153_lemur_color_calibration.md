---
title: "lemur color calibration"
date: 2012-09-02
forum: System76 Support
---

### Post by even5 on 2012-09-02
I'm just getting set up on a new lemur ultra.  It seems to me that the colors on the display are washed out.  I've looked at all the display intensity levels, but the washed-out effect is present at all light levels.  There are references to calibrating the colors of the monitor (sorry, I forget where I saw that), but the choices are the system76 driver, which is in use, or a custom set of calibrations.  Is there a description of how to set up color calibrations?  A tool to help do it?

Thanks for any info!

---

### Post by brdmn on 2012-09-02
> **even5 said:**
> I'm just getting set up on a new lemur ultra.  It seems to me that the colors on the display are washed out.  I've looked at all the display intensity levels, but the washed-out effect is present at all light levels.  There are references to calibrating the colors of the monitor (sorry, I forget where I saw that), but the choices are the system76 driver, which is in use, or a custom set of calibrations.  Is there a description of how to set up color calibrations?  A tool to help do it?

Thanks for any info!

It's not the most precise approach, but I just use xgamma to tweak the gamma until the colors seem less washed out.  In my case, I set the gamma to 0.7.

---

### Post by even5 on 2012-09-03
The "xgamma -gamma 0.5" command does improve things a little, but there is still the effect of a white film over the screen.  It is like the effect when editing the colors in a photo in digikam, and setting the brightness and/or gamma high without setting the contrast higher.

I'll keep looking.  Thanks for the suggestion.

---

### Post by even5 on 2012-09-05
I find that the angle of the laptop screen makes a big difference -- if it is tilted back more than I expected, the colors are intense and clear.  I think this issue is solved.

---

### Post by brdmn on 2012-09-05
Cool, thanks.  I'm still trying to learn about these different types of displays, but based on personal experience, the matte display on my Thinkpad T410i is significantly better than the glossy one on the lemU4, in terms of being susceptible to the angle of the screen as well as the "washed out colors" issue.  Hopefully, the lemU5 will come with a better screen!

---

