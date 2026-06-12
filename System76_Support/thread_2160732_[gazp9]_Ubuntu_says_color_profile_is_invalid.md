---
title: "[gazp9] Ubuntu says color profile is invalid"
date: 2013-07-08
forum: System76 Support
---

### Post by rorschachwalter on 2013-07-08
In Color settings, the System76-provided color profile yields this message:

> The profile has the following problems:
• One or more of the primaries are invalid

Did System76 mess up with calibration, or is GNOME messing up somehow?

---

### Post by isantop on 2013-07-09
Did you download the correct color profile for your screen? If you have the glossy display, you can't use the ColorPro profile.

---

### Post by rorschachwalter on 2013-07-09
I have the IPS matte display. I did a fresh install, so I downloaded the color profile from this [Knowledge76 page]("http://knowledge76.com/index.php/GazP9").

When I run the System76 Driver, it produces a color profile named "System76 15.6" ColorPro IPS Matte Display".

When I install the profile I copied from the machine when I originally received it, there are apparently two profiles to choose from -- edid-6c4c6b27d0a90b99322e487510455230.icc and edid-c947f1e0543c3d5eb0ce7e891fdfbe91.icc. The first seems to install "Gazelle Professional", the second "LG TV". I'm guessing those were automatically generated from the display and from me testing the HDMI output on an LG TV.

The difference between the other two and "System76 15.6" ColorPro IPS Matte Display" is quite noticeable. Also when checking the to/from sRGB tabs, the difference between the images is noticeable, whereas the LG TV profile yields minimal difference. Wouldn't a properly calibrated profile to yield minimal difference??

**To summarize:**
_Gazelle Professional_
*Error?*: No error.
*Size*: 1.6 kB
*File*: ~/.local/share/icc/edid-6c4c6b27d0a90b99322e487510455230.icc
*Origin*: Seems to be created by default
*To/From sRGB*: Significant differences

_LG TV_
*Error?*: No error.
*Size*: 1.8 kB
*File*: ~/.local/share/icc/edid-c947f1e0543c3d5eb0ce7e891fdfbe91.icc
*Origin*: Was found on original installation, I made a backup of it just incase. Installed manually on fresh installation.
*To/From sRGB*: Minimal differences

_System76 15.6" ColorPro IPS Matte Display_
*Error?*: The profile has the following problems:
&#8226; One or more of the primaries are invalid
*Size*: 24.5 kB
*File*: /var/lib/colord/icc/system76-gazp9-ips-matte.icc
*Origin*: System76 Driver installs it.
*To/From sRGB*: Significant differences
*Comment*: The first two profiles aren't noticeably different when switching between them. This profile, however, is very different.


Which is the correctly calibrated profile? I'm guessing the last one is correct, but it's strange to me that it is less accurate with regards to sRGB than the LG TV option is, and that it's giving an error about an invalid primary.

---

### Post by isantop on 2013-07-09
Ubuntu automatically generates a basic color profile based on the EDID information. That's the two you're seeing. The calibrated profile is the last one, and that's the one you want. 

The reason the LG profile isn't showing significant differences is because it isn't calibrated. Remember that those images demonstrate differences, rather then show actual changes in gamut (Which is impossible to show via example). The To/From images show the error of the uncalibrated display vs. the output with the profile. It can also mean that the LG TV is fairly well calibrated from the factory (which is common for TVs).

---

### Post by rorschachwalter on 2013-07-09
So that still leaves two questions:
1) If the Syste76 profile is calibrated, why is the To/From change so noticeable for that profile?
2) Why is GNOME giving me an error with that one?

---

### Post by isantop on 2013-07-10
> **rorschachwalter said:**
> 1) If the Syste76 profile is calibrated, why is the To/From change so noticeable for that profile?
Because those images show the differences in the color input/output versus an uncalibrated display. That basically means that the color without the profile is significantly different in output from the color with the profile applied.

> **rorschachwalter said:**
> 2) Why is GNOME giving me an error with that one?
It may be related to the Colorhug calibration process. We're looking into better calibration hardware for future profiles.

Are you able to apply the profile? Which version of Ubuntu are you using?

---

### Post by rorschachwalter on 2013-07-10
I am able to apply the profile just fine. The error only shows up at the bottom of the View Details modal for that profile.

I'm using an up-to-date Ubuntu GNOME 13.04 (with the GNOME 3 ppa and System76 Driver) running kernel 3.8.0-26.

---

### Post by isantop on 2013-07-11
I see. As long as the profile is applied correctly, I don't think you need to worry.

---

