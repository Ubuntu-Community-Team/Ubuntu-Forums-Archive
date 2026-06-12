---
title: "Hardware trouble on Gazelle Perf"
date: 2007-08-12
forum: System76 Support
---

### Post by klato on 2007-08-12
OK this thread is going to involve 2 different hardware issues with my gazp2.

1)

I only get sound out of the right speaker on my system76 Gazelle Performance (gazp2).

I'm not sure when it started, but I noticed it probably about a week ago.  I've tried messing around with the mixer settings both by double clicking on the volume control and also by running 'alsamixer' from a terminal, but it still doesn't work.  My external speakers work fine though.

2) 

The CD-RW drive on this thing hasn't worked right since day 1.  I stick in a cd, and nothing happens.  No icon on the desktop, nothing in Places, nada.  Sometimes however, when I boot with a blank cd, I can see a 'Blank CD-RW' icon on the desktop, but it doesn't want to burn at all.


I've looked around but haven't found a solution to either of these problems.  So basically my question is: do I have faulty hardware and should I send it back to system76?

Thanks!

---

### Post by thomasaaron on 2007-08-13
> I only get sound out of the right speaker on my system76 Gazelle Performance (gazp2).

I'm not sure when it started, but I noticed it probably about a week ago. I've tried messing around with the mixer settings both by double clicking on the volume control and also by running 'alsamixer' from a terminal, but it still doesn't work. My external speakers work fine though.

In the volume control, underneath the sliders, there are little "chain links." Clicking on them causes the links to break and connect. Make sure none of them are broken. Breaking them might cause one side to play and not the other (in theory). 


> The CD-RW drive on this thing hasn't worked right since day 1. I stick in a cd, and nothing happens. No icon on the desktop, nothing in Places, nada. Sometimes however, when I boot with a blank cd, I can see a 'Blank CD-RW' icon on the desktop, but it doesn't want to burn at all.

1. Reseat the CD drive. There is a single screw on the bottom that holds it in. (It's the one in the shallow recessed hole, not the deeply recessed hole.) Pop the drive open, remove the screw, pull the drive out, push the drive firmly back in, replace the screw.

If this doesn't work, please post the output of this command:
ls /media

---

### Post by klato on 2007-08-13
Thanks for the response.

About the volume:

I checked the chain links and they are all connected and set to the max.  Apparently I'm using the "HDA Intel (Alsa mixer)".  None of them are muted.

About the CD drive:

I unscrewed it and reseated it, but it still behaves erratically.  I just popped out the blank disc, and popped it back in, and the blank cd icon doesn't show up anymore, but it was there when I booted.

Output of 'ls /media':
cdrom  cdrom0

Also, just for the hell of it, I ran the System76 Driver 2.0.5, rebooted, but no change.

---

### Post by thomasaaron on 2007-08-14
Well, if you can get both channels from external speakers but not from the computer's internal speakers, I'm thinking you've blown a speaker?


As for the CDRom, can you boot from a live CD? This would tell us (to an extent) if the CD drive is good or bad. If it will not boot from a live CD, you should go ahead and contact me at support[at]system76[dot]com.

---

### Post by klato on 2007-08-14
OK I was able to boot from the CD, but the experience was a little strange...

My wireless didn't work at all (although it detected wireless networks in the area, I flat out couldn't connect to my home network).  There were also missing icons all over the place in the top gnome panel menus.  I eventually rebooted, but when it asked me to remove my live CD,  I couldn't get the drive door open.  I had to shut down with the power button, turn it back on, and then pop the cd out before the system booted.

---

### Post by klato on 2007-08-19
bump

---

### Post by thomasaaron on 2007-08-20
OK. It looks, then, like your CD drive is working, at least to some extent.

But, if it is not putting an icon on the Desktop, it is probably bad.

Send me an email, and we'll get another one out to you.

---

