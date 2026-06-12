---
title: "Ugly display on HDTV with Nvidia Geforce on Quantal"
date: 2012-07-03
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Yahoé on 2012-07-03
This fully updated Quantal amd64 is connected to a 55'' HDTV via a Geforce210.
 Whatever the resolution (1980x1080 now) I get a very bad display quality. The workspace is wider than then screen, and Unity is mostly hidden. I have tried installing Nvidia-current to no avail.
Booting from a 12.10 Daily Live USB gives me the same result, but booting from a 12.04 Daily Live USB gives me a perfect picture.
Any idea what is happening to this Quantal system?

Regards

---

### Post by ScislaC on 2012-07-03
Quantal's version of the NVIDIA driver is now using xrandr if I'm not mistaken, so it could be related to that.

---

### Post by cariboo on 2012-07-03
Have you tried setting the TV to just scan?

---

### Post by Yahoé on 2012-07-03
Further test: as mentioned, booting from a 12.04 Live USB gives me a perfect image, but if I install 12.04 on a spare partition, upon reboot 12.04 gives me the same ugly display.

II could add that on Quantal, if I boot the PC with the built in Radeon HD4xxx rather than the Nvidia PCIE card, the display is there again perfect. So it's rather certain that the HDTV is not the cause.

A neighbour uses Quantal with an HDTV and a Nvidia card running the latest nvidia-current and it's all working just fine for him.

---

### Post by Cheltspy on 2012-07-03
The Overscan Compensation bar has gone and is not working on 302.17.

This is a real problem for older HDTVs.

I want to revert to driver 295.53 and no longer can.[IMG]http://ubuntuforums.org/images/icons/icon13.gif[/IMG]

---

### Post by Yahoé on 2012-07-17
Does any one have any new idea on how to obtain a clear display on this brand new LED HDTV?
Nouveau or the latest Nvidia blob both give the same poor result. Someone mentioned xrandr, does anyone no more about this? Help would be greatly appreciated.

---

### Post by dino99 on 2012-07-18
watch edgers ppa and their comments on top

---

### Post by effenberg0x0 on 2012-07-18
I have a home media server that is connected to two LED 46 TVs (the sort of standard XBMC, SickBeard, Sabnzbd+, 2 LIRC for Infrared receivers running as daemons setup) plus one 19" touchscreen monitor (cheap LCD), all running on two NVidia 9600GT. All my content is 720p/1080p and runs flawlessly. The server has a bluray drive that outputs to the displays too.

My main desktop is connected to two Dell LED+IPS 27" using a single NVidia GTS450 and also to a LG 23" and a LG 16" (both TN) on a NVidia 9500. High res content runs perfect too.

One thing I have noticed though is that the image is much more detailed (hard to explain: colors look more vivid, contrast is better, there's no "Ghost Effect", like if I had a higher refresh rate) when connecting the displays (TVs and Monitors) via DVI instead of HDMI. I have even tried Monster Cable HDMI-1.4 cables and any cheap DVI still works better here for any content. I have tried all possible adjustments on the displays (but I didn't go as far as trying to use spectrometers/colorimeters - as I said, I'm not a pro on video). 

All displays work beautifully with HDMI when connected to XBOX 360 / PS3 or a standalone bluray player. The weird video is clearly exclusive to Ubuntu machines with NVidias, any driver version.  

As I have no idea why this happens, and I know anything about video, I have simply abolished the use of HDMI here. I have noticed this about a year ago with these same TVs, monitors and cards.

So, maybe if you have a spare DVI cable lying around, you could give it try. It's just a guess anyway.

Regards,
Effenberg0x0

---

### Post by Yahoé on 2012-07-19
> **dino99 said:**
> watch edgers ppa and their comments on top

Thanks for the input but right now I have the problem on a freshly installed Quantal, I don't the edgers ppa and I fail to see how these comments relate to my problem.

---

### Post by Yahoé on 2012-07-21
> **effenberg0x0 said:**
> I have a home media server that is connected to two LED 46 TVs (the sort of standard XBMC, SickBeard, Sabnzbd+, 2 LIRC for Infrared receivers running as daemons setup) plus one 19" touchscreen monitor (cheap LCD), all running on two NVidia 9600GT. All my content is 720p/1080p and runs flawlessly. The server has a bluray drive that outputs to the displays too.

My main desktop is connected to two Dell LED+IPS 27" using a single NVidia GTS450 and also to a LG 23" and a LG 16" (both TN) on a NVidia 9500. High res content runs perfect too.

One thing I have noticed though is that the image is much more detailed (hard to explain: colors look more vivid, contrast is better, there's no "Ghost Effect", like if I had a higher refresh rate) when connecting the displays (TVs and Monitors) via DVI instead of HDMI. I have even tried Monster Cable HDMI-1.4 cables and any cheap DVI still works better here for any content. I have tried all possible adjustments on the displays (but I didn't go as far as trying to use spectrometers/colorimeters - as I said, I'm not a pro on video). 

All displays work beautifully with HDMI when connected to XBOX 360 / PS3 or a standalone bluray player. The weird video is clearly exclusive to Ubuntu machines with NVidias, any driver version.  

As I have no idea why this happens, and I know anything about video, I have simply abolished the use of HDMI here. I have noticed this about a year ago with these same TVs, monitors and cards.

So, maybe if you have a spare DVI cable lying around, you could give it try. It's just a guess anyway.

Regards,
Effenberg0x0

Thanks [effenberg0x0]("http://ubuntuforums.org/member.php?u=260143") I just had not thought of using the DVI out. So I got a VDI-to HDMI connector but it did not make a difference.
Finally I just swapped the video card for a Radeon and it's working just fine.
I then tested the Nvidia video card on a different Ubuntu 12.10 rig also connected to a HDTV from the same brand, and it's working beautilfully there!!! Go figure. So maybe it had something to do with this model of HDTV.

Thanks anyhow.

---

