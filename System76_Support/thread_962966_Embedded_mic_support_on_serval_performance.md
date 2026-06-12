---
title: "Embedded mic support on serval performance"
date: 2008-10-29
forum: System76 Support
---

### Post by andrewdied on 2008-10-29
(Very similar to the camera question.)

I started testing skype, and briefly got something recorded.  It's all done, though, and I'm not getting anything recorded from the internal mics.  

What input device is it?  It looks like I have the choices of:
[LIST][*]Front mic boost[*]Line in boost[*]Mic boost[*]Capture[*]Digital


[/LIST]

The follow on question is what input device is the audio mic input on the side?

The last thing I did (before my brief success) was follow this thread: [http://ubuntuforums.org/showthread.php?t=268652](http://ubuntuforums.org/showthread.php?t=268652), which had me do:
# sudo alsactl names
# sudo alsactl store
# sudo reboot

---

### Post by thomasaaron on 2008-10-30
Here are the internal mic settings for Sound Recorder.

Make sure you've run your System76 driver and rebooted.

---

### Post by andrewdied on 2008-10-31
My second two screenshots looked the same, so I suppose I'm good there.  I hadn't installed the gnome alsamixer program, so I did that.  It does look a tad different, such as I'm using the Realtek sound card rather than the alsa driver.  I didn't see a way to move that to alsa, though.  Does that matter?  (Well, since I still can't record off the internal mics, I suppose so.)

Screenshot attached.

---

### Post by thomasaaron on 2008-10-31
```
I'm using the Realtek sound card rather than the alsa driver. I didn't see a way to move that to alsa, though. Does that matter?
```

Yes, you need to be on ALSA. On your sound control panel (the one you just posted), go to File > Devices > ALSA.

---

### Post by andrewdied on 2008-11-15
> **thomasaaron said:**
> ```
I'm using the Realtek sound card rather than the alsa driver. I didn't see a way to move that to alsa, though. Does that matter?
```

Yes, you need to be on ALSA. On your sound control panel (the one you just posted), go to File > Devices > ALSA.

gnome-alsamixer just has File > Exit on my computer.  The preferences only shows the Realtek ALC268, too -- no Alsa.  Here's a screenshot.  Are there any specific packages I need installed?  I have the system76 driver loaded, obviously.

---

### Post by thomasaaron on 2008-11-17
> gnome-alsamixer just has File > Exit on my computer. The preferences only shows the Realtek ALC268, too -- no Alsa. 

Double-click your speaker icon. It will produce a window. In that window, go to File-Devices and select the ALSA mixer.

Nevermind. I see you are using Xubuntu (which we don't support). Your going to have to figure out how to get it set to ALSA. That is definitely your problem.

The Serval is a pretty powerful machine. Why use a minimalist OS? Just curious.

---

### Post by andrewdied on 2008-11-18
> **thomasaaron said:**
> Double-click your speaker icon. It will produce a window. In that window, go to File-Devices and select the ALSA mixer.

Nevermind. I see you are using Xubuntu (which we don't support). Your going to have to figure out how to get it set to ALSA. That is definitely your problem.

The Serval is a pretty powerful machine. Why use a minimalist OS? Just curious.

Ah, from previous screenshots I thought you were using gnome-alsamixer.  That looks different from the gnome volume control, so I'll give that a run.

I'm actually using ubuntu with xfce.  I'll log things as ubuntu rather than xubuntu, since that's confusing the issue.  I installed the laptop with the 8.04 ubuntu CD, then put on the system76 driver as is good and right and true.

I try to use the window manager-ish things that I need the features from.  Jiggly windows are cool (and my daughter ooed and aahed over them about 30 minutes ago), but I've used Xfce in years past and liked it.  I like vertically maximizing windows, which is easy in Xfce and requires a little more work in gnome.

Heck, when I worked at Jabber I used ion3, which is *definitely* far on the minimalist scale.  I could setup each of the windows just how I wanted them, making more terminals was really easy, and flipping between desktops was even easier.  As a home computer, though, a little more pizzaz is OK.

---

### Post by williamson389 on 2008-11-25
I am also experiencing no response from my internal mic.  i checked my specs with those in the snapshots and they are the same, just soundrecorder will freeze up if i try it.  Any ideas?  i know this is a common problem but i have already been through most of the walkthroughs with no sucsess.
i am running Hardy Heron (64bit) on an Acer Aspire 5100.  i have alsa installed.

---

### Post by thomasaaron on 2008-11-26
Williamson, this forum is for supporting System76 laptops. Not that we are unwilling to be helpful, but just so you know, we don't have any Acers to test with. 

You might try going to System > Preferences > Sound and making sure all of the dropdowns are set to ALSA.

---

### Post by williamson389 on 2008-11-26
oops sorry.

---

