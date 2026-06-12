---
title: "64 -bit Lightning"
date: 2012-07-30
forum: Ubuntuzilla
---

### Post by verstehnix on 2012-07-30
I'm running Thunderbird 14.0 on the amd64 version of Ubuntu 10.04 LTS and desperately searching for a suitable version of the Lightning extension. Being too dumb to build it myself I'd appreciate any help.

Thanks,
-Dieter

---

### Post by nanotube on 2012-07-31
Hi,
This page has some links to 64bit lightning builds:
[http://kb.mozillazine.org/64_bit_builds](http://kb.mozillazine.org/64_bit_builds)

Unless you want a really old 64bit build, you probably will want the latest nightly build, from here:
[http://ftp.mozilla.org/pub/mozilla.org/calendar/lightning/nightly/latest-comm-central/linux64-xpi/](http://ftp.mozilla.org/pub/mozilla.org/calendar/lightning/nightly/latest-comm-central/linux64-xpi/)

---

### Post by levlaz on 2012-07-31
Which version of Thunderbird are you using? 

Lightning tends to be very finiky when showing up in the add-ons section.

---

### Post by verstehnix on 2012-07-31
Thanks a lot for your quick answer. Unfortunately none of those versions worked for me. Some were refused by Thunderbird because they are not compatible (Thunderbird 14.0 seems to need Lightning 1.6), others were loaded but all Lightning buttons were greyed out (32 bit versions?)). I'll probably have to switch back to an older combination. 
It's not easy to find the right time for updating a software package...

---

### Post by nanotube on 2012-07-31
well the nightly builds should be of the 'latest version'.
if those don't work, i might suggest asking on mozilla forums also.

---

### Post by verstehnix on 2012-08-04
Well, I don't know why, but here is how it finally worked:

[LIST=1]
[*]de-installed Thunderbird,
[*]renamed ~/.thunderbird
[*]renamed ~/.mozilla-thunderbird
[*]re-installed Thunderbird from ubuntuzilla
[*]downloaded and installed LIghtning from /pub/mozilla.org/mozilla.org/calendar/lightning/candidates/1.6-candidates/build1/linux-x86_64
[/LIST]
The key were probably steps 2. and 3.: I had to get rid of any old configuration. Of course I lost all profiles and had to re-configure everything from ground up. But at the end this took less time than all the fiddling around before.
Hope this helps people having the same problem.

-Dieter

---

