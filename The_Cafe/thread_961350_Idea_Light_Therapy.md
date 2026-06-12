---
title: "Idea: Light Therapy"
date: 2008-10-28
forum: The Cafe
---

### Post by Thelasko on 2008-10-28
With the days getting shorter, I'm experiencing some problems staying alert during the morning hours.  I suspect this is because the sun is no longer up when I get ready for work in the morning.

[The Mayo Clinic]("http://www.mayoclinic.com/health/seasonal-affective-disorder-treatment/DN00013") suggests using light therapy to correct this issue.  In the past, light therapy was performed with high intensity light bulbs, but it's recently been discovered that low intensity blue light can have the same effect.  

I'm thinking about creating a program/script for my machine that displays blue light on the monitor to create a similar effect.  I will run it as a cron job so it will start running when I wake up.  It will also start out low in intensity and get brighter over several minutes.

Does anybody have some suggestions on how I should do this?  Do you think it will work?

---

### Post by puppy on 2008-10-28
Possibly, but the light has to be the right wavelength for it to 'fool' your body into thinking its being bathed in nice natural light :)  

I think the blue bulbs you're talking about are known as 'daylight' bulbs, and I also have a friend who suffers from manic depression who uses lightbox therapy - the very intense light you mention. Actually having been in the same room as one of these light boxes I can attest to the fact that somehow they do make you feel more relaxed etc - weird huh?

---

### Post by Thelasko on 2008-10-28
The catch is, does the light actually have to be that specific (479nm) wavelength, or can we approximate it with RGB?  Most human eyes can only see [three wavelengths]("http://en.wikipedia.org/wiki/Trichromacy") (~560,530,420 nm) so why go through the expense to produce a wavelength that can't be detected by the human eye?  Why not [approximate]("http://www.artdim.com/EBV_download/waveRGBcolor.pdf") it with RGB?

The RGB approximation of 479nm in RGB is 0,228,255.

---

