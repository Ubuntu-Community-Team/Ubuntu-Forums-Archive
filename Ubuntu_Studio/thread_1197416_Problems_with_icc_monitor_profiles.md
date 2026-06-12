---
title: "Problems with icc monitor profiles"
date: 2009-06-26
forum: Ubuntu Studio
---

### Post by jenschr on 2009-06-26
I calibrate and profile my monitor with Spyder I and PhotoCal. It works well under WindowsXP, and the profile (gamma) is loaded in the LUT at startup.

But the profile doesn't work under Ubuntu. I can load the testprofile "bluish.icc", and nobody will doubt that it's loaded! But my own profile is just passed silently by xcalib.

The profile seems not to have a vcgt-tag with the gamma information. So the PhotoCal loader perhaps loads the gamma some other way under Windows.

The missing vcgt-tag is confirmed by an error message from the dispwin loader in the Argyll set of utilities.

So my first question is, if somebody have experience with the Spyder I / PhotoCal combination - working or not working?

And second - and more important - are profiles from the later Spyderversions (and of course their driverprograms) working under Ubuntu?

I don't have an absolute need to get the calibration process to run in Ubuntu (though it would be nice) but the profiles should work.

The Spyder is relative cheap, and the newer ones can calibrate and profile projectors, which is important to me.

Thank you very much in advance - I really hope to get rid of Windows, but calibrating and profiling the monitor is a must.

Jens Chr. Jensen

---

### Post by jenschr on 2009-06-26
Sorry - wrong forum. I can't delete the post, so I hope this will do.

Jens Chr. Jensen

---

