---
title: "Capture Video With Black Magic Intensity Pro"
date: 2009-11-21
forum: Ubuntu Studio
---

### Post by thursdayy on 2009-11-21
I have downloaded and installed the drivers and made sure it is working and running properly.

The only thing I can't find is a program that will record from it.  Anyone has any suggestions on which programs to use?

FYI:
Windows 7 / Ubuntu 9.10 dual boot
Intel Ci7 920
1TB - Partitioned for Windows 7 and Ubuntu
750GB - Backup
3TB Raid 0
12GB DDR3 RAM

Also, how do I make it that I can view and use my RAID system.  It works fine in Windows but now in Ubuntu which is a first.  (P.S. Asus Rampage II does not have any linux drivers for any RAID software)

Thanks a lot guys, I tried searching the forums/google but have found nothing except old articles of people complaining that blackmagic has never made any linux drivers.  Now that there is drivers I can't seem to find a good program that can utilize the device.  Kino doesn't work because it uses firewire.  I tried KDenLive but I can't seem to get video4linux2 to work? I have no clue on how to use FFMPEG from the command line.  Any other suggestions?  I tried installing cinelerra but it did not appear in my applications -> sound and video> tab.

---

### Post by thursdayy on 2009-11-21
Never mind, I'm an idiot.  They already have a program I can interface with to record.  My only concern now is how am I able to view the RAID drive?  I can see it in Windows but not on Ubuntu.

---

### Post by tk2kewl on 2010-03-03
I am looking to buy one of these.... did you figure out your RAID issue?

---

### Post by gst-kaps on 2010-05-31
Now its easy to capture from the Blackmagic Intensity Cards on Linux , by using the blackmagic gstreamer source , made available by Media-Magic Technologies. More info @  [http://mediamagictechnologies.com/products.html](http://mediamagictechnologies.com/products.html) :)

---

### Post by Jake007g on 2010-06-01
I thought the BlackMagic supported Linux anyway?

---

### Post by gst-kaps on 2010-06-02
Sure Blackmagic supports Linux drivers, but I was mentioning about the gstreamer plugin that would help the user to capture blackmagic data in gstreamer applications seemlessly.

---

### Post by lukeiamyourfather on 2010-06-29
> **gst-kaps said:**
> Sure Blackmagic supports Linux drivers, but I was mentioning about the gstreamer plugin that would help the user to capture blackmagic data in gstreamer applications seemlessly.

How expensive is the GStreamer plugin for the Intensity card? Looks interesting but they don't list any prices. You know what they say, if you have to ask, its too expensive.

---

### Post by gst-kaps on 2010-06-29
The Plugin is not expensive, and its not from Blackmagic Design but from company named Media-Magic Technologies. You can try sending a request to [email]business@mediamagictechnologies.com[/email]

---

### Post by Nausser on 2010-07-01
I am interested in utilizing the Blackmagic Intensity Pro as well. I currently need component capture abilities; however, I feel the HDMI input will come in handy as well with future shooting. I've used Cinellera a bit and enjoy some of it's features. I wish I could know ahead of time which products will work with this card. If us as a Linux community can get this card well integrated with Ubuntu or Ubuntu Studio, we will have made the final huge step to considering Ubuntu as an un-compromising alternative to proprietary Apple and Windows based products. True professional video editing/finishing will be the last leg of the "Linux as a production solution" rise to popularity.
Autodesk Smoke has been running on Linux for years and is the pinnacle of video editing, allthough very specific on it's host OS Linux flavor and hardware specs. Having this Intensity Pro card fully integrated into professional editing available for any Linux flavor would give any professional absolutely no reason to look anywhere else.

I became excited when I learned Linux was supported as noted on the Blackmagic website for the Intensity Pro. I was a bit less excited when I've been reading mixed reviews on the card's actual integration with available editing applications.
If anyone has any first hand experience with this card, I would love to know how it all has went. I'm trying to collect several data points while planning my system build.

---

### Post by gst-kaps on 2010-07-02
Nausser, the blackmagic intensity card , seems to work well . I am able to do synchronous audio-video capture & playback using the blackmagic gstreamer plugin, mentioned above.

---

### Post by lukeiamyourfather on 2010-07-02
> **Nausser said:**
> I am interested in utilizing the Blackmagic Intensity Pro as well. I currently need component capture abilities; however, I feel the HDMI input will come in handy as well with future shooting. I've used Cinellera a bit and enjoy some of it's features. I wish I could know ahead of time which products will work with this card. If us as a Linux community can get this card well integrated with Ubuntu or Ubuntu Studio, we will have made the final huge step to considering Ubuntu as an un-compromising alternative to proprietary Apple and Windows based products. True professional video editing/finishing will be the last leg of the "Linux as a production solution" rise to popularity.
Autodesk Smoke has been running on Linux for years and is the pinnacle of video editing, allthough very specific on it's host OS Linux flavor and hardware specs. Having this Intensity Pro card fully integrated into professional editing available for any Linux flavor would give any professional absolutely no reason to look anywhere else.

I became excited when I learned Linux was supported as noted on the Blackmagic website for the Intensity Pro. I was a bit less excited when I've been reading mixed reviews on the card's actual integration with available editing applications.
If anyone has any first hand experience with this card, I would love to know how it all has went. I'm trying to collect several data points while planning my system build.

If you don't mind using the included "Media Express" package from Black Magic then it works, though it won't directly integrate with anything else in Linux. I was pretty disappointed to find out it didn't support GStreamer framework out of the box. The plugin to use the card with GStreamer from that Media Magic company will cost more than half what the card itself costs.

---

### Post by DMJC on 2011-04-14
There's a free gstreamer plugin now sitting in the official gstreamer repository under gst-plugins-bad. I hope this helps. KDEnlive also has support for the card.

---

### Post by Desti on 2011-08-20
> **DMJC said:**
> There's a free gstreamer plugin now sitting in the official gstreamer repository under gst-plugins-bad. I hope this helps. KDEnlive also has support for the card.

  Hi, what element do you mean?  It's a other, then the one from the University of Helsinki?! [http://opencast.jira.com/wiki/display/MH/Blackmagic+Design+Intensity+Pro+%28PCIe%29+HDMI](http://opencast.jira.com/wiki/display/MH/Blackmagic+Design+Intensity+Pro+%28PCIe%29+HDMI)

---

### Post by dannyboy79 on 2012-11-27
very interested in this for capturing my xbox 360 gameplay.

---

### Post by hatsch on 2013-01-07
The MLT Framework supports capturing from Decklink and Inensity Pro devices.

so capturing with BM Intensity Pro in ubuntu is as easy as:

```
sudo apt-get install melt
```

```
melt decklink: -consumer avformat:myfile.mp4
```

you can find a list of available options for the avformat consumer  here: [http://www.mltframework.org/bin/view/MLT/ConsumerAvformat](http://www.mltframework.org/bin/view/MLT/ConsumerAvformat)

---

### Post by dannyboy79 on 2013-01-07
if people are interested in a GUI to capture from the Intensity Pro you can use kdenlive as it's built on melt. I suggest sunab's PPA, he has 2 different ones. Either the kdenlive-release (which is very stable) or his kdenlive-svn (which is experimental from git)

---

### Post by ineedmunchies on 2013-01-16
> **DMJC said:**
> There's a free gstreamer plugin now sitting in the official gstreamer repository under gst-plugins-bad. I hope this helps. KDEnlive also has support for the card.

Took me a good bit more searching after seeing this post. But the gstreamer plugin is called decklink and works with the intensity pro.

My pipeline to view video from SD pal composite source:


```
gst-launch-0.10 -v decklinksrc mode=2 connection=4 ! ffmpegcolorspace ! xvimagesink sync=false
```

To check out the other modes: 

gst-inspect-0.10 decklinksrc

---

