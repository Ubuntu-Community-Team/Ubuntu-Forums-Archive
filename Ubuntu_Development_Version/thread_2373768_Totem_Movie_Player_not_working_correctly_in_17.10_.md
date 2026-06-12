---
title: "Totem Movie Player not working correctly in 17.10 Beta 2"
date: 2017-10-09
forum: Ubuntu Development Version
---

### Post by jadaube2 on 2017-10-09
I did a fresh install of Ubuntu 17.10 Beta 2 on my laptop - Dell Inspiron N4110, Intel Sandybridge Mobile Graphics, Intel® Core™ i3-2350M CPU @ 2.30GHz × 4, 6GB of RAM.  If I try to play ANY video on the Totem movie player (the default GNOME player), I get sound and subtitles but no picture. VLC works just fine. This did not happen on my previous 14.04 install on the same laptop. Is this a beta OS bug or just a bad media player?

---

### Post by dino99 on 2017-10-09
Try to get warning/error from either:
- into a terminal: journalctl | grep totem
- into a terminal, run totem and play a video: you may get some comments added

Seems you are not alone: [https://bugs.launchpad.net/ubuntu/+source/gstreamer1.0/+bug/1722319](https://bugs.launchpad.net/ubuntu/+source/gstreamer1.0/+bug/1722319)

---

### Post by mc4man on 2017-10-09
what happens if you remove the gstreamer1.0-vaapi plugin?

---

### Post by jadaube2 on 2017-10-13
Hmmm - well the problem seems to have resolved itself since I updated yesterday, but I don't remember any Totem-specific updates. Now all the files I have play just fine.

---

### Post by Frogs Hair on 2017-10-13
I was using VLC, but Totem seems to work after recent updates. I had a green fog in the player though I could hear the audio.

---

### Post by P-I H on 2017-10-13
After I used Ubuntu Software to enable GStreamer from the ugly and bad plugin sets Totem worked OK.
VLC worked OK after I unchecked  Accelerated video output (Overlay) and Widow decorations and selected OpenGL  GLX  video output (XCB)

---

### Post by ventrical on 2017-10-13
Worked out of the box here.

---

### Post by jadaube2 on 2017-10-13
OK - problem is not as solved as I thought - I had logged into ubuntu on Xorg and forgot to change it back.  Totem works fine in Ubuntu on Xorg, but I only get sound when I log into regular Ubuntu (Wayland, i think)

---

### Post by Frogs Hair on 2017-10-13
> **jadaube2 said:**
> OK - problem is not as solved as I thought - I had logged into ubuntu on Xorg and forgot to change it back.  Totem works fine in Ubuntu on Xorg, but I only get sound when I log into regular Ubuntu (Wayland, i think)

I tried on Xorg also, I'll check wayland.

---

### Post by Frogs Hair on 2017-10-13
Tested Wayland with Totem & VLC using the same DVD . Totem is still broken here.

---

### Post by mc4man on 2017-10-13
> **Frogs Hair said:**
> Tested Wayland with Totem & VLC using the same DVD . Totem is still broken here.
In general wayland & multimedia  are still a deficient mix, particularly if hwdec is involved.
What's seen here is dvd video will flicker with a green screen if the gst-vaapi plugin is installed when using a ubuntu session.
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1723565](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1723565)

---

### Post by ventrical on 2017-10-14
Plays mpgs in wayland  but can't find codecs for wmv files.

---

### Post by mc4man on 2017-10-14
> **ventrical said:**
> Plays mpgs in wayland  but can't find codecs for wmv files.

Noticed last week, forgot about.. so,
[https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/1723599](https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/1723599)

---

### Post by Frogs Hair on 2017-10-14
> **mc4man said:**
> In general wayland & multimedia  are still a deficient mix, particularly if hwdec is involved.
What's seen here is dvd video will flicker with a green screen if the gst-vaapi plugin is installed when using a ubuntu session.
[https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1723565](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/1723565)
 Confirmed and added screenshot.

---

