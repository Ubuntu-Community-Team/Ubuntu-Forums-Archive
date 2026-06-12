---
title: "Building an Ubuntu-based MythTV System Using Raspberry Pi"
date: 2017-04-28
forum: The Cafe
---

### Post by UbuntuWho on 2017-04-28
*I didn't know where to bring this up, so I'm starting in the Cafe. Mods, if you have an appropriate place for this discussion, please move this thread! Thank you!*

So, I'm considering building a DVR-like system using a Raspberry Pi. According to their website ([https://www.mythtv.org/wiki/Raspberry_Pi#Overview](https://www.mythtv.org/wiki/Raspberry_Pi#Overview)), MythTV requires Raspberry Pi version 2 or above. I'm wondering just what I need to get a good system working using a Raspberry Pi, Ubuntu as the OS, MythTV software, and my cable provider. Any suggestions?

---

### Post by TheFu on 2017-04-28
I think any R-pi will be under powered and not have sufficient I/O for many of the great reasons people choose MythTV.  Do you want automatic commercial removal or transcoding to files that are 75% smaller?  No r-pi can do that. 

Don't miss understand, you can use a r-pi as a playback device. Works well, for specific types of content.

You can also use a r-pi to record 1 show at a time if the tuner that works in your location is like mine.  What is needed to record cable or OTA varies greatly depending on your location.  I'm in the USA and only record broadcast TV. It uses ATSC, which is mpeg2 TS.  Because of the extremely limited disk I/O capabilities, I only record 1 show at a time with my Pi. That effectively is just saving a network stream to a file, nothing more.
A $50 intel pentium CPU on a $50 motherboard in a $20 case with a $40 hdd can do so much more than any R-pi can dream, as far as a back-end server is concerned.  The amount of I/O supported by almost any amd/intel MB will be 1000x more than a raspberry pi. It really is an I/O issue.
If you just want to watch live TV on a r-pi, I can confirm that you don't need mythtv, at least in the USA, for OTA broadcasts.

Fired comcast about 5 yrs ago here. Mostly people who like live, popular, sports or live 80+ miles from a metro area still need cable. Everyone else can probably drop cable.

In the USA, there is an HDHomerun Prime network tuner that supports cable TV using a CableCARD.  I thought the DRM only worked with Windows, but could be wrong. [https://www.silicondust.com/product/hdhomerun-prime/](https://www.silicondust.com/product/hdhomerun-prime/) seems to say it works fine with Kodi and their software. [https://www.mythtv.org/wiki/Silicondust_HDHomeRun_Prime](https://www.mythtv.org/wiki/Silicondust_HDHomeRun_Prime) 

I own 3 HDHomerun devices - each with 2 internal tuners. 2 or older models that don't work easily with Linux, but 1 is a newer HDHR4-US which is a DLNA server. To access a specific channel is just telling any player to play a stream from a channel specific URL. It is very nice, provided the playback device can handle mpeg2 playback.  Hidef mpeg2 content requires the r-pi MPEG license to work.

I think in different parts of the world, they have moved to h.264 or h.265 for their TV.  No raspberry pi today can handle hidef content using h.265 video codes. Just not enough CPU power and zero GPU support for that codec (at this time).

Is there a mythtv or multimedia subforum here? Those folks might have closer first-hand knowledge.

Anyway, hope this is helpful in some way.

---

### Post by UbuntuWho on 2017-04-28
Let's assume we're talking the most powerful Raspberry Pi you can get. I want my system to do a lot while still having a low profile. Pretty much a do-it-yourself kind of thing. Is it possible? I'm not trying to disregard your message, TheFu, but I need info from someone who has tried multiple minimal computers. If Raspberry Pi isn't the answer, perhaps you might suggest another alternative? :-?

---

### Post by TheFu on 2017-04-28
Did you read that link you posted?  It is suggesting a r-pi for a front-end.  That is completely fine, but you still must have a myth backend.  Nobody is suggesting that a raspberry-pi (any sort) can be a mythtv backend.

If you don't want a backend, then you can't use myth.  You can use Kodi with a PVR plugin on a Raspberry pi, however. 

Who is your CATV provider? Where are you located? There are different standards around the world.

---

### Post by UbuntuWho on 2017-04-29
Okay, just took a look at the links, TheFu. Very interesting. I'll take a look into it, but I'm still leaving this open for more suggestions.

I also didn't notice the part where the Raspberry Pi was just the frontend. I assumed it could do it all! :-P However, the fact that it needs a tuner makes sense.

---

### Post by speedwell68 on 2017-04-30
> **TheFu said:**
> I think in different parts of the world, they have moved to h.264 or h.265 for their TV.  No raspberry pi today can handle hidef content using h.265 video codes. Just not enough CPU power and zero GPU support for that codec (at this time).

From what I have read on the Kodi forums H.265 is now possible on an RPI3 with a suitable overclock.  Not tried it myself as I don't have a Raspberry Pi 3.  I didn't bother upgrading my RPI2 or RPIBs as there was no improvement in video playback at the time.

---

