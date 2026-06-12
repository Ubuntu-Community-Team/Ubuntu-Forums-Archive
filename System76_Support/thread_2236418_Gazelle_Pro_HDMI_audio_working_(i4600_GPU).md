---
title: "Gazelle Pro HDMI audio working (i4600 GPU)"
date: 2014-07-26
forum: System76 Support
---

### Post by allcoms on 2014-07-26
Hi

I thought I'd let you know I've got HDMI audio working properly (no break-ups, distortion or overly high pitch) on my Gazelle Pro.

I'm running the latest KXStudio (Ubuntu 14.04) but I've installed the 3.15.6 lowlatency kernel from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15.6-utopic/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.15.6-utopic/)

Then I had to select hw:HDMI,7 [HDMI 1] as my audio output device under Cadence and that was it - I now have a fully functional Linux laptop!

NB HDMI audio output did not work correctly with the standard 14.04 3.13.x kernel

---

