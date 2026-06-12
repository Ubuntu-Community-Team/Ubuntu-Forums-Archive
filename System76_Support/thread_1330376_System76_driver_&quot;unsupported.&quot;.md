---
title: "System76 driver &quot;unsupported.&quot;"
date: 2009-11-18
forum: System76 Support
---

### Post by Makurosu on 2009-11-18
I just purchased a System76 Meerkat Ion NetTop preinstalled with Karmic 32-bit.  When I try to run the System76 driver from the System -> Administration menu, it says:

"Unsupported

This driver is designed for System76 machines running Ubuntu versions 6.06 through 9.10.  If you have a System76 machine running one of the above Ubuntu versions please file a bug report at https://launchpad.net/system76"

I ran update and got the latest version, and it still does this even after restarting.

I don't know if this has been addressed previously, but what can I do to resolve this?  I'm using a Panasonic plasma TV at 1920x1080 via HDMI.  I get no sound yet and playing movies at 1080p is very jerky, but I imagine these issues will be resolved once I can get the System76 driver working.  Everything else seems to be working fine so far otherwise.

---

### Post by HotShotDJ on 2009-11-18
I can't really help you with the System76 driver... but I might be able to help you with the jerky video --

First, you need to make sure you have the nvidia driver activated through System -> Administration -> Hardware Drivers.  This is not handled by the System76 drivers.  Then install mplayer, if you haven't already.  Then try to play a movie in it.  You MIGHT get an error.  If you do (actually, even if you don't), go to ~/.mplayer/gui-config and look for the line that starts with "vo_driver = " and make sure it reads as follows:```
vo_driver = "vdpau"
```Now try playing your video in MPlayer again.  Please post back and let us know if this helps.

---

### Post by Makurosu on 2009-11-18
Thanks for your help.  I did what you said, and it's less jerky but still plays about 7-8 frames per second.  Also, I got an mplayer error saying that there were too many packets in the video buffer.  I'm on my way to work now, and I'll get back to it tonight.

---

### Post by thomasaaron on 2009-11-18
Keep working on the video issue here, but email me regarding the System76 Driver, and we'll figure it out. support...at...system76...dot...com.

---

### Post by thomasaaron on 2009-11-18
Edit...
Nevermind.

---

### Post by HotShotDJ on 2009-11-21
> **Makurosu said:**
> Thanks for your help.  I did what you said, and it's less jerky but still plays about 7-8 frames per second.I've been doing some more reading on using vdpau in karmic... and at the moment, I am not convinced that this mode is fully enabled in any of the video players, including mplayer -- even though the option is available and doesn't throw any errors in mplayer.

Much of the information that I'm finding in my searches is contradictory. The general consensus seems to be that mplayer must be specially compiled in order to get vdpau support, and even with that, the methods I've been reading are contradictory and produce inconsistent results.  Unfortunately, I don't have any 1080p movie files to test, nor do I have any HDMI devices.

There is no question in my mind that vdpau is the solution to your problem.  What is unclear (at least to me) is how to implement this solution in Karmic.

---

### Post by Makurosu on 2009-11-21
I just got 1080p video working this afternoon.  Someone in another forun on this website showed me how to do it.  Follow the instructions here:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)

I played a 1080p h.264 .mkv video earlier and it was using about 20% of one of the CPU's.  I still have not figured out how to get HDMI audio, but it looks like the Meerkat Ion Nettop is perfectly capable of being an HTPC.  Maybe the necessary drivers will be incorporated in to the next stock version of Ubuntu.

---

### Post by HotShotDJ on 2009-11-21
> **Makurosu said:**
> I just got 1080p video working this afternoon.  Someone in another forun on this website showed me how to do it.  Follow the instructions here:

[https://launchpad.net/~nvidia-vdpau/+archive/ppa](https://launchpad.net/~nvidia-vdpau/+archive/ppa)Excellent!  Thank you for posting your solution. :)

---

