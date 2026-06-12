---
title: "white-purple screen when computer shut down (with video)"
date: 2009-04-25
forum: System76 Support
---

### Post by formol on 2009-04-25
hi, 

i saw this problem before, but I was able to avoid it using the "restricted driver" instead of the original nVidia driver.

now with Jaunty, it's in both, at different scale

here is a video I make to be sure to describe the problem as clearly as possible : [http://www.youtube.com/watch?v=kusm1htw1UE]("http://www.youtube.com/watch?v=kusm1htw1UE")

at the end of the video, when the computer should down, the monitor became white and turn violet/purple.  then the computer shut down.

with the driver from the nVidia website, 180.51 for x64 (NVIDIA-Linux-x86_64-180.51-pkg2.run), it's the same thing but the screen turn progressively into purple/violet around the border and the computer don't shut down alone. 

otherwise, my monitor don't seems to be broken or anything like that, when the computer is on, color are as they should be. 

my computer is : Pangolin panp4n with a GeForce 9300 GS with the default monitor 

in conclusion, what does that mean? does it is normal?  it scared me a little bit when I saw that for the first time...

---

### Post by thomasaaron on 2009-04-25
Hi, Formol.

Posting on youtube was a great idea. That was very helpful.

You should never have to install nVidia drivers from nVidia's website. Doing this tends to hose configurations and is very difficult and time-intensive to fix. 

Whenever you need restricted drivers for nVidia, it's best to get them from Ubuntu's repositories (i.e. from System > Administration > Hardware Drivers).

So, I'd recommend completely un-doing anything you've done with the the nVidia drivers, all configs, etc... Then see if you can load it from Hardware Drivers.

Also, did you upgrade to Jaunty, or did you do a fresh install?

---

### Post by formol on 2009-04-26
for this video, I had
- install a fresh 9.04 x64 Ubuntu
- update & upgrade
- install the system76 driver
- install nVidia driver in the terminal
- observe that the white/purple screen was there and the computer didn't shut down alone
- remove the nVidia driver in the terminal
- install the restricted driver
- film it and post it

now, more surprisingly maybe, I got another video.  I erased everything and re-install Jaunty-x64, update & upgrade.  then I shut it down and the white/purple screen was there for at least 30 seconde before I pressed the on/off button. so I wanted to film it, it gave this : [http://www.youtube.com/watch?v=3vzhX7xAvp0]("http://www.youtube.com/watch?v=3vzhX7xAvp0")

since, i've start and shut down my laptop number of this, it always give result identical as the video video I posted.

---

### Post by abulluck on 2009-04-27
I have a Panpv4 and when I "upgraded" to the beta 9.04 and used the nvidia 180 I got the same white/purple screen that sometimes required a hard shut down to get out of.

I recently did a fresh install and went back to the prior nvidia driver (173 I think) and I no longer get freezes at the white/purple screen anymore.

I do however get a white screen on shutdown that will stay up for a second or two.  Not a big deal, but just not clean/professional looking.  

I am happy now that I don't get freezes, but I will stay tuned to this thread for a "white screen on shutdown" fix.

---

### Post by Lee_Machine on 2009-04-27
I have had the same issue on my Panp4n since the beta. I have not re-installed since the final release, but have kept all updates current.

Again not a big issue here.

---

### Post by formol on 2009-04-27
I uninstalled the 180 nVidia driver and installed the 173.  same thing. 2 or 3 secondes of white/purple screen before computer shut down. 

> **Lee_Machine said:**
> 
Again not a big issue here.

I partialy agree : yes, it's not very bad in itself.  the problem came that maybe, let say, 1 time on 10, I have to push the off/on button when the computer get freeze in this white/purple windows.  and after a couple time like that, i got error message at boot that my /home was not correctly unmount and I've to run fsck for like 3 or 4 minutes.  and I confirm, after a couple of those fsck scan, I lose my /home  (it happen now 2 time, that I had to re-install everything because of that.
even if, I could boot on a live-cd to copy my files, it would not see it while normal boot process. 

anyway, at least, my monitor is not damaged.

---

### Post by thomasaaron on 2009-04-27
OK, we've duplicated this on a Serval here in the shop. The 173 driver keeps it from hanging.

Definitely an nVidia bug.

---

### Post by formol on 2009-04-27
yeah, that's what I tought.

then, now, what can I or we do?  spam nVidia with link to this forum?

---

### Post by thomasaaron on 2009-04-28
There may already be a bug out on it. But if not, file a bug against nvidia-glx-180 and maybe one against nvidia-glx-173 too.

But I imagine this is already on their radar.

---

