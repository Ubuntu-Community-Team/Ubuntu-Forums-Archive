---
title: "Meerkat HDMI video suddenly blanking"
date: 2017-05-30
forum: System76 Support
---

### Post by mike.feldman on 2017-05-30
I've had a Meerkat i5 tall case for a few days, and I bought it an Acer 4K display which I've connected via HDMI cable.  Out-of-Box experience was pretty good ... there was no audio to the monitor's speakers over HDMI when first powered up, but plugging/unplugging an 1/8" audio plug into the headphone jack on the front of the Meerkat resulted in audio working.  But that's not my issue ...

After plugging in an external USB DVD drive (ISO9660 CD-R disk mounted OK on 2nd try) and ejecting the disk, I was browsing some support sites when the screen blanked ... it was like the power saver kicked in.  I moved the mouse and hit a key and the display came back on, but then it continued to blank every 10 seconds or so ... very hard to get any reading done.  After suffering through trying to surf with something less than a 50% duty cycle on the display, I powered down.

My question is this a know problem?  Anyone seen it before?  If not, are there any suggestions on diagnosis?  How can I quickly tell if the problem is software, flakey NUC hardware or a flakey display monitor.  I do have another monitor I can try, but I'm not sure I can drive the Acer monitor from any other machine on hand.

-- Mike

---

### Post by mike.feldman on 2017-05-31
I searched the Acer user forums and folks seemed to have similar problems when running the monitor at 3840x2160@60 with less than quality cables.  In my case I was using the HDMI cable that came with monitor.  If the monitor loses sync, it searches the three input ports, looking at HDMI last.  I got through most of today without display problems.  I just suspended the system, and the monitor went to low power mode, came back when I resumed, and now I'm back into the cycle of the screen blanking every 30 seconds for 5 seconds.

One odd thing I noticed is that the Brightness & Lock Systems Settings panel had the blank display timer set to 1 minute (I remember setting it to 10 minutes!) and now I've changed it to never and I'm still trapped in the 30 second blanking cycle.  It's as if I had 2 runaway instances of the screen blanker running on the shortest cycle.

-- Mike

---

### Post by mike.feldman on 2017-06-03
I went a few days with no blanking problem, then it was back immediately upon playing a YouTube video in Firefox.  That's probably the 1st time I've used audio output to the Acer monitor in that time.  I notice that blanking in this episode happened on any mouse movement.  To recover, I suspended the machine.  I have yet to try a different HDMI cable.  It's plausible that audio on top of 3840x2160 video pushes my Acer supplied HDMI cable to the breaking point.

I'll keep this thread alive to report my observations as I learn more about the problem.

---

### Post by april-system76 on 2017-06-05
Hi Mike,

I've been seeing this on a handful of other systems as well, all Intel-based, and all recent. It feels like an Intel HD graphics issue or kernel issue, but I can't quite get it figured out. Can you share the output of:

uname -a
dpkg -l |grep linux-firmware
dpkg -l |grep intel

---

