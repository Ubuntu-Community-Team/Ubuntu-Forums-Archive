---
title: "(RANT) Sound on linux"
date: 2009-07-27
forum: The Cafe
---

### Post by Eviltechie on 2009-07-27
I'm so upset right now. I was trying to get jack to work with pulseaudio so that I could get jack to work with my microphone, but in the process of setting it up, I seem to have made everything worse. Now jack dosen't even start. This is a good example of "One step forward, two steps back". It didn't help that the ubuntu devs left out the "pulseaudio-module-jack" package for some reason, so I had to install from a ppa. I think I'm going to go ahead an reinstall ubuntu, seeing that I'm going to get a major hardware upgrade this week.

---

### Post by MaxIBoy on 2009-07-27
I know what your problem is. You're using pulseaudio.

Try using OSS4 (not OSS3, which is what comes with Ubuntu.) Takes about an hour to setup ALSA, Pulseaudio, Gstreamer, etc. so that they will all redirect to OSS4 instead. Also you need to replace the volume control applet on your panel with a different one.

Once that's done, you will never have a sound problem again. Ever. :popcorn:

Just download the OSS .deb from this location:
[http://www.4front-tech.com/release/oss-linux-4.1-1052_i386.deb](http://www.4front-tech.com/release/oss-linux-4.1-1052_i386.deb)
Run the installer. It will fail the first time, that's okay. Just reboot and run it again, the second time it will work. 


These two pages will be helpful:
[http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4)
[http://www.opensound.com/wiki/index.php/Tips_And_Tricks](http://www.opensound.com/wiki/index.php/Tips_And_Tricks)
Of particular interest are the directions for "alsa emulation," gstreamer, and pulseaudio emulation. Set up those three things, maybe ten minutes each, and 90% of applications are working already.


DISCLAIMER: This post was based on PERSONAL EXPERIENCE ONLY, your mileage may vary. But if you have problems, I'd be glad to help.

---

### Post by SunnyRabbiera on 2009-07-27
For me Pulse does work but the distro I use plays a big part of it.
On Ubuntu usually OSS is the best though with Jaunty Pulse is pretty nice.
On OpenSuse Pulse is great
On Mandriva Alsa seems to be the winner.
Pulse is still young, but its shaping up to be a great sound system, a few more fixes here and there and pulse can surpass almost all sound systems.
OSS4 is cool too but the push for Pulse is far greater.

---

### Post by MaxIBoy on 2009-07-27
Even if they finally cobble it together to the point where it'll work, it's still a mess.

This is Pulseaudio (not including the operating system API and the soundcards) :
[IMG]http://3.bp.blogspot.com/_vLES3KKBdaM/SjsQ-mZzETI/AAAAAAAAAF8/iBdrRxsDycQ/s320/pulse.png[/IMG]

This is OSS4:
[IMG]http://1.bp.blogspot.com/_vLES3KKBdaM/SjsQ-d_yg6I/AAAAAAAAAF0/JU4mG0IdV-s/s320/oss.png[/IMG]

They both do the same job, OSS4 does it better, and Pulseaudio is more complex and error-prone.


Seriously, people. OSS4 is already finished and working. Pulseaudio is currently on fire and skidding down the runway, having failed to take off. (Okay, it's not *that* drastic, but still.)


This is a good read if you're interested in this stuff:
[http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html](http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html)

---

### Post by HappinessNow on 2009-07-27
> **MaxIBoy said:**
> I know what your problem is. You're using pulseaudio.

Try using OSS4 (not OSS3, which is what comes with Ubuntu.) Takes about an hour to setup ALSA, Pulseaudio, Gstreamer, etc. so that they will all redirect to OSS4 instead. Also you need to replace the volume control applet on your panel with a different one.

Once that's done, you will never have a sound problem again. Ever. :popcorn:

Just download the OSS .deb from this location:
[http://www.4front-tech.com/release/oss-linux-4.1-1052_i386.deb](http://www.4front-tech.com/release/oss-linux-4.1-1052_i386.deb)
Run the installer. It will fail the first time, that's okay. Just reboot and run it again, the second time it will work. 


These two pages will be helpful:
[http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4](http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4)
[http://www.opensound.com/wiki/index.php/Tips_And_Tricks](http://www.opensound.com/wiki/index.php/Tips_And_Tricks)
Of particular interest are the directions for "alsa emulation," gstreamer, and pulseaudio emulation. Set up those three things, maybe ten minutes each, and 90% of applications are working already.


DISCLAIMER: This post was based on PERSONAL EXPERIENCE ONLY, your mileage may vary. But if you have problems, I'd be glad to help.

> **MaxIBoy said:**
> Even if they finally cobble it together to the point where it'll work, it's still a mess.

This is Pulseaudio (not including the operating system API and the soundcards) :
[IMG]http://3.bp.blogspot.com/_vLES3KKBdaM/SjsQ-mZzETI/AAAAAAAAAF8/iBdrRxsDycQ/s320/pulse.png[/IMG]

This is OSS4:
[IMG]http://1.bp.blogspot.com/_vLES3KKBdaM/SjsQ-d_yg6I/AAAAAAAAAF0/JU4mG0IdV-s/s320/oss.png[/IMG]

They both do the same job, OSS4 does it better, and Pulseaudio is more complex and error-prone.


Seriously, people. OSS4 is already finished and working. Pulseaudio is currently on fire and skidding down the runway, having failed to take off. (Okay, it's not *that* drastic, but still.)


This is a good read if you're interested in this stuff:
[http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html](http://insanecoding.blogspot.com/2009/06/state-of-sound-in-linux-not-so-sorry.html)

Wow! that is very intense and helpful, Thanks!

---

### Post by Bucky Ball on 2009-07-27
Yea, thanks for that.

---

