---
title: "Which one is the most lightware video player ?"
date: 2015-07-04
forum: Ubuntu, Linux and OS Chat
---

### Post by Xpdin on 2015-07-04
Which one is the most lightware video player ?

I watch usually normal videos, with not so high resolution...

Referring to the hardware resources used tell me please do you recommend me a video player which comes with the most common codecs included, or is it possible to use a fast way in Linux to download/install the video and audio codec that I need for the video which I am trying to watch?

If this is possible how can I find in Linux the video codec which I need to see the video?

One of the most important option included would be to search and download subtitles for the video which I am watching to (would be better to search on more subtitles websites).

Thank you.

---

### Post by kerry_s on 2015-07-04
for codecs install "ubuntu-restricted-extras"

for player that already has codecs, i think vlc

whats wrong with the default player installed ?

---

### Post by monkeybrain20122 on 2015-07-04
I think you meant "lightweight"?

For lightweight mpv. If graphic card supports it you can use hardware decoding  with it. codecs have nothing to with player, except maybe vlc which seems to have some additional codecs bundled, but it is not "lightweight"

---

### Post by Bucky Ball on 2015-07-04
*Thread moved to **Ubuntu, Linux and OS Chat**.*

As with your thread regarding the lightest torrent client. Have you had a search? You give no indication in either thread that you've researched for the lightest or found any clues. Asking 'what is the lightest <add app here>' will garner a lot of opinions and beliefs. Asking questions about specific apps will still get plenty of opinions but also support with your issue and some factual answers.

Good luck. :)

---

### Post by mc4man on 2015-07-04
regarding subs search. Supposedly a vlc extension can do that, haven't used. Note it is for vlc 2.0 or 2.2, Not 2.1, uses opensubtitles.org
info, instr. here
[http://www.maketecheasier.com/get-vlc-to-download-subtitles/](http://www.maketecheasier.com/get-vlc-to-download-subtitles/)
(or bsplayer - windows, $30

---

### Post by v3.xx on 2015-07-04
You do not say, but I wonder if you could also be in need of a graphic driver.

Could you post your specs?
```
sudo apt-get install inxi && inxi -b
```

---

### Post by monkeybrain20122 on 2015-07-04
> **mc4man said:**
> regarding subs search. Supposedly a vlc extension can do that, haven't used. Note it is for vlc 2.0 or 2.2, Not 2.1, uses opensubtitles.org
info, instr. here
[http://www.maketecheasier.com/get-vlc-to-download-subtitles/](http://www.maketecheasier.com/get-vlc-to-download-subtitles/)
(or bsplayer - windows, $30

  For 2.2.1 I have to download the extension from videolan, the built in one doesn't work. Forgot where the link is, but can google for it.

---

### Post by Xpdin on 2015-07-05
> **v3.xx said:**
> You do not say, but I wonder if you could also be in need of a graphic driver.

Could you post your specs?
```
sudo apt-get install inxi && inxi -b
```


```
         System:    Host: xlbtx Kernel: 3.13.0-55-generic i686 (32 bit) Desktop: LXDE (Openbox 3.5.2) Distro: Ubuntu 14.04 trustyMachine:   System: Hewlett-Packard (portable) product: N/A version: F.09
           Mobo: Hewlett-Packard model: 30D7 version: KBC Version 83.12
           Bios: Hewlett-Packard version: 68MDD Ver. F.09 date: 01/11/2008
CPU:       Dual core Intel Pentium Dual CPU T2390 (-MCP-) clocked at 800.00 MHz 
Graphics:  Card: Advanced Micro Devices [AMD/ATI] RV516/M62-S [Mobility Radeon X1350] 
           X.Org: 1.15.1 drivers: ati,radeon (unloaded: fbdev,vesa) Resolution: 1024x768@59.9hz 
           GLX Renderer: Gallium 0.4 on ATI RV515 GLX Version: 2.1 Mesa 10.1.3
Network:   Card-1: Broadcom BCM4311 802.11a/b/g driver: b43-pci-bridge 
           Card-2: Intel 82562GT 10/100 Network Connection driver: e1000e 
Drives:    HDD Total Size: 250.1GB (1.4% used)
Info:      Processes: 154 Uptime: 1 day Memory: 829.4/2015.6MB Client: Shell (bash) inxi: 1.9.17          
```

Regards,

---

### Post by v3.xx on 2015-07-05
Your graphics is supported by the open source driver.
[http://manpages.ubuntu.com/manpages/lucid/man4/radeonhd.4.html](http://manpages.ubuntu.com/manpages/lucid/man4/radeonhd.4.html)

But from what I make from this
[http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)
There is no 3D support, but your running lxde, so you probably do not care about that.  Anyhow, it looks like no driver issue.

With dual core and 2G of ram, you should be able to run vlc, default, or other players without issue.  Maybe totem or mplayer?
[https://help.ubuntu.com/community/MultimediaApplications](https://help.ubuntu.com/community/MultimediaApplications)

But again, I would think vlc would run.

Good luck :)

---

### Post by SeijiSensei on 2015-07-05
SMPlayer, the graphical front-end for mplayer and mpv, has a built-in function to search at opensubtitles.org.  I've never used it because I watch Matroska files with the subtitles included as a "stream."  SMPlayer also makes it easy to try out different video drivers via Options > Preferences > General > Video.

I don't think video players will differ much in "weight."  The biggest effect on memory is the player engine.  Pushing a 720p H.264-encoded file with 10-bit color through mpv eats up about 350 MB of memory, half what firefox is currently using.  Still playing that same file with mplayer uses about 110 MB, but the playback itself (over wifi) isn't nearly as smooth as mpv's.  VLC used about 170 MB.  Its playback was better than mplayer's, but still not as smooth as with mpv.

None of those figures are all that large compared to a 2 GB physical memory space and, presumably, at least that much allocated to swap.

Of course, as always, "your mileage may vary."

---

### Post by Xpdin on 2015-07-05
Thank you very much for your time, and very good recommendations...

Excuse me, maybe my reason with the old laptop is wrong... it is not very old, but still...

I hope and would be glad if you would understand me and my psychology of liking the simple, smooth, light things, in this instance the installed programs. 
      Maybe even if I would have one of the most performant computer I would like to use the applications with the features which I need, or as close as possible features to my needs. 

In this situation, is it allowed(against the forum rules) to ask questions here on the forum regarding my little "obsession" if there are not any other real(grounded) reasons, like an old hardware configuration?

Have a wonderful week.

---

