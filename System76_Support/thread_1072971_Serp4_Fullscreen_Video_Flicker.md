---
title: "Serp4 Fullscreen Video Flicker"
date: 2009-02-17
forum: System76 Support
---

### Post by globose on 2009-02-17
I think I own a Serp4 (or Serp 3???).  Whenever I play any videos in Fullscreen, (especially online), I can see as the frames switch horizontal line flickers.  I would think that having a NVIDA graphics card should easily handle fullscreen video.  I don't know if I'm supposed to adjust the refresh rate somewhere?  Any help would be appreciated.

---

### Post by thomasaaron on 2009-02-18
Could it be a slow Internet connection? Is this with a wired or wireless connection?

---

### Post by Lee_Machine on 2009-02-18
Are you referring to Flash Videos in Full screen? What version of flash are you running? In V9 and below you can sometimes get choppy videos in fullscreen. 

To check for your flash version in firefox type about : plugins in the address bar. (minus the spaces)

Or does it happen with videos in Mplayer too?

---

### Post by globose on 2009-03-01
Thank you both for your responses.  Sorry I'm slow to respond; I am still figuring out how to have the forums automatically email me if I get responses.

I don't think the problem is my internet connection or flash, because I can download a file like [elephants dream]("http://orange.blender.org/download") and play it in mPlayer, and it still happens.  It also does it if I play a DVD.  Also, I have a fast internet connection, and flash version is 10.0.

The flicker is most noticeable if something fast is happening on the screen.  If the scene is slow, you don't really see it.  The flicker is really brief, but it still annoys me. As far as I can tell, I've always had this problem, even after a clean install of Ubuntu.  I just think there is something not right with my NVIDIA settings or maybe the driver isn't quite right?

I see in Synaptic that I have NVIDIA-glx-177 driver installed, but there is also NVIDIA-glx-180 available.  Is the 180 one better?  Which one should I have? I also see under "System > Administration > Hardware Drivers" menu that the 173 driver is also available.

My display also doesn't resume after suspend.  I get a blank screen for a really long time, and then I get a command line error (I'll try it now and then post as an edit). I'm not sure if the two problems are related.

I've determined my Graphics card using ```
lspci
``` to be:

VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)

Thanks again

---

### Post by globose on 2009-03-01
When I try to resume from suspend, I get a flash of my desktop, and then it switches to a black screen, where my hard drive just chugs.  If I ctl+alt+backspace, it switches to showing command line errors scrolling up the screen really fast, but they all are something like this:

> ata 3.00: status: {DRDY ERR }
ata 3.00: error:  {ABRT }
ata 3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata 3.00: cmd c4/00:08:07:7d:8e:00:00:00:00/00:00:00:00/e0 Emask 0x1 (device error)

I think this may be referring to the hard drive, so maybe this is an independent problem I need to work on.

---

### Post by thomasaaron on 2009-03-02
Two things to try:

1. Turn off your desktop effects (System > Prefs > Appearance > Visual Effects > None.

If that doesn't fix it, open a terminal and run this command...

gstreamer-properties

Under the Video tab, set the first drop-down selector to "X Window System (No XV)". 

You may need to reboot after that.

---

### Post by globose on 2009-04-05
Turning off desktop effects seemed to help some, but not fix it completely.  As I've been investigating the problem, I'm realizing that the biggest problem is running Flash, especially on HULU.com.  After some searching, I found that I am running an alpha version of the 64-bit adobe flash, since the only other alternative is to run the 32-bit version with a wrapper. It seems like the consensus online is that the native alpha version is better than the 32-bit wrapped version.  

All in all, I guess the lines are tolerable if I turn desktop effects off and watch the lower-resolution (360) version on hulu.  Thanks for all your help.  I'll wait until a stable release of 64-bit adobe flash comes out before I re-investigate the problem.

---

### Post by thomasaaron on 2009-04-06
Did you try the gstreamer-properties instructions?

---

### Post by globose on 2009-04-06
I did, but it didn't help.

---

### Post by thomasaaron on 2009-04-06
Try re-installing Flash. It should upgrade to the latest version automatically.

sudo apt-get --purge remove flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

Restart firefox.

---

