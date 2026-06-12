---
title: "Can't setup 5.1 optical out"
date: 2021-11-21
forum: Ubuntu Development Version
---

### Post by Yahoé on 2021-11-21
Hi, This is not specific to Jammy, but I'm on Jammy. I can't seem to enable the S/PDIF optical output in 5.1. Stereo works, but not 5.1. I use pavucontrol to switch, but I get no sound out. Does any one have any experience to share, has been successful in doing so? The motherboard is a Maximus VIII Gene, ES9023P HD audio, HDA Intel PCH, 100 Series/C230 Series Chipset Family HD Audio Controller Thanks

---

### Post by TheFu on 2021-11-22
Does 5.1 work over HDMI?  Just curious.  I have a little device that accepts HDMI in, then splits the video to send to a projector and sends the audio to a receiver for processing there.  I just don't have long enough toslink cables and didn't want to run different cables over long distances. The projector run is already 20ft.

---

### Post by Yahoé on 2021-11-22
Yes, 5.1 works over HDMI.

---

### Post by TheFu on 2021-11-23
[https://askubuntu.com/questions/1098666/iec958-s-pdif-not-working](https://askubuntu.com/questions/1098666/iec958-s-pdif-not-working) has an answer based on the audio codec support in the advance options of pavucontrol. Definitely worth a double-check.
[ATTACH=CONFIG]289532[/ATTACH]
See the different checkboxes?

---

### Post by Yahoé on 2021-11-23
Thanks, TheFu. iec958-stereo (S/PDIF optical) works for me, it's just iec958-ac3-surround-51 that doesn't. I see the check boxes when I select iec958-stereo as output, but not for iec958-ac3-surround-51

---

### Post by TheFu on 2021-11-23
Perhaps the correct drivers/codecs aren't installed?  I think the link above shows some packages to be installed.  But IDK. I've never used SPDIF out from a computer directly.

---

### Post by Yahoé on 2021-11-24
Yes, all packages are installed, hence my question. Thank for trying to help though TheFu :-)

---

