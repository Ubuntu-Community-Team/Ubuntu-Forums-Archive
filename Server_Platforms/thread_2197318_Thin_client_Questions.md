---
title: "Thin client Questions"
date: 2014-01-03
forum: Server Platforms
---

### Post by mrbill2 on 2014-01-03
Im looking to set up a thin client network, but am not sure on how to best set things up.

Ive got a couple of windows embedded thin client devices, as well as a couple of lower end desktop machines (no hdd, ~1 ghz cpu, 512 ram)
All are connected to a gigabit network.

Im not really sure on how to best set things up. Is it possible to get smooth video playback on the clients? Just being able to play video in a media player smoothly should be enough, although if Its possible smooth performance of a flash video in a browser / smooth complex websites would be great.

Ive been using just the built in rdp client of the windows embeded machines so far. Works well enough for simple stuff. word processing, remotely configuring the machine, and basic web sites, but get to anything with lots of moving banners or animation and it grinds to a crawl / stutters badly.

any help is appreciated.

---

### Post by TheFu on 2014-01-03
VDI is the industry term for this.  Usually video performance is the issue, but most business clients don't need that. When they do, they install proprietary codecs onto each client and ensure the video drivers support whatever video codecs are needed.

Most low-end CPUs that doesn't have GPU support for video decoding cannot handle 720p or higher video without stuttering even locally. I know this from trying to get a Via C7 and Atom N270 to do it.

If all you need is a video player, spending your effort to setup a plex server for the house and use either a roku or Chromecast ($35) is probably a better use of time - though both of those have some MAJOR issues.  A more flexible solution for viewing videos is a $150 XBMC device.  Mine is an AMD E350-APU, a few GB RAM, used HDD, with microPSU (silent), connected to a TV and projector over HDMI.

If you don't need video, then the **LTSP** is a good place to start.  Dropping video as "a requirement" opens many other options.

When I travel, I take a low-end netbook and use NX to remote back home when I need more than ssh. NX uses ssh, so it is very secure. Even on a GigE LAN, most remote desktop solutions (all free ones) don't handle video very well.  I've looked at RDP, NX, VNC, and Spice ... none deal with video perfectly - though Spice does handle audio the best that I've seen.  It was not acceptable in other ways.

---

### Post by mrbill2 on 2014-01-03
Darn. not what i was hoping to hear. I understand that hd video will not stream well on older devices. Most of my older machines video hardware doesnt support over a 1024x768 resolution, so i would probally never try passing a video of larger size than that to them. Most of the stuff is sd 4:3 video,  the size of the monitors ive had on hand.

Ill look around some more and post back with what solution I use.

thanks for the advice.

---

### Post by TheFu on 2014-01-03
> **mrbill2 said:**
> Darn. not what i was hoping to hear. I understand that hd video will not stream well on older devices. Most of my older machines video hardware doesnt support over a 1024x768 resolution, so i would probally never try passing a video of larger size than that to them. Most of the stuff is sd 4:3 video,  the size of the monitors ive had on hand.

Ill look around some more and post back with what solution I use.

thanks for the advice.

Whoa there. It isn't all that bad news.  Streaming a desktop is hard. Playing local video can be relatively easy, if the machines have good enough GPU support and a modest-for-today CPU.  Any Core2Duo can handle 720p playback in software, but with only 512MB of RAM, I suspect your machines are more like Pentium4-class.

On the video card side, older cards didn't support OpenGL 2.x and later, so much of the hardware-based video playback we take for granted just isn't possible.  My netbook had enough GPU to run XBMC, but the GPU didn't support HW-based video accel.  All video playback happened in the CPU and that was limited to about 600p.  DVDs are 480p and I would transcode anything at higher resolution down to 480p before going on travel.  Transcoding on a netbook (Atom n270) took over 24 hrs for a single 2 hr movie - I didn't have enough time to wait until completion. On a old Core i7 (not current gen), it takes about 90 minutes.

So, if you can make the files available to the clients - perhaps using NFS - and have low enough resolution on the video so the CPUs can handle local playback, then video life won't be so bad. These old machines really have a GigE wired ethernet card?

If you post the exact CPUs, exact GPUs, then folks here might be able to suggest video resolutions to target.  As another  example, I used to travel with a Nokia N800 (4inch Linux on ARM).  It couldn't playback 480p content at all, but ... let me look for my transcode script ...  at 208p and 15fps, it was watchable on airplanes.

I've got no solution for Flash or HTML5, sorry.

---

