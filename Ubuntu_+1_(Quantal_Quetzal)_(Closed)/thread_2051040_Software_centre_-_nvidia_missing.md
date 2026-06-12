---
title: "Software centre - nvidia missing"
date: 2012-09-01
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by Elfy on 2012-09-01
At the risk of being told to search - I did ;)

As far as I know my card should still have an available driver - but since the move of additional drivers to software sources - nothing appears to be there for the card.

Some light shined on some long forgotten thread here would be of enormous help :)

GeForce 8500 GT

---

### Post by xeizo on 2012-09-01
sudo apt-get install nvidia-current should install your driver

---

### Post by mc4man on 2012-09-01
The Additional Drivers window has been empty since Aug 7, at least for nvidia hardware.

[1034746]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1034746")
[1044725]("https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/1044725")

(I probably should dupe one to the other, atm don't feel like it

---

### Post by effenberg0x0 on 2012-09-01
> **Elfy said:**
> At the risk of being told to search - I did ;)

As far as I know my card should still have an available driver - but since the move of additional drivers to software sources - nothing appears to be there for the card.

Some light shined on some long forgotten thread here would be of enormous help :)

GeForce 8500 GT

Piskie, I'm using the proprietary installer this cycle, it's working fine. I have posted wget links at [http://ubuntuforums.org/showthread.php?t=2042119&page=5](http://ubuntuforums.org/showthread.php?t=2042119&page=5) post #45.

Regards,
Effenberg

---

### Post by P-I H on 2012-09-01
I used Synaptic to install nvidia-current

---

### Post by mc4man on 2012-09-02
At least here have tracked the missing anything in Add. drivers with nvidia to the change in the nvidia-current/nvidia-current-updates package list in early Aug
This was added in the Depends:
xorg-video-abi-11 | xorg-video-abi-12 | xorg-video-abi-13

It seems ubuntu-drivers will only look at the 1st one so nothing is shown
editing it back to just xorg-video-abi-13 & Add. then shows nvidia-current & nouveau
( editing files in /var/lib/apt/lists/ is not really advised as a mistake will prove costly till corrected & apt-get update will overwrite anyway
Noted in current report so hopefully will be fixed in some manner

---

### Post by mc4man on 2012-09-05
All the bugs concerning  this have been duped to an older bug on "NVidia driver in Quantal not compatible with X.org/kernel"

I guess i'm totally missing something here - most recent comment by M.Pitt has me a bit 'confused'

In regards to the current 12.10 nvidia-current packages - 
> But they won't work, so it makes little sense, and is even dangerous, to show them when they don't work. ubuntu-drivers-common quite deliberately hides them.

Even though I generally use nouveau on this laptop it seems that the times I've had nvidia installed all was well. 

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1033222](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/1033222)

---

### Post by effenberg0x0 on 2012-09-05
I got my main desktop on QQ/nvidia proprietary 304.43 and a GTS450. 
My secondary desktop is running QQ/nvidia proprietary 304.43 for a 9800GT and a 9500GT.

My home media server is running QQ/nvidia proprietary 304.43 with a GTX550ti I installed a few days ago

I have never installed nvidia-current except for testing. nvidia-current* packages are blacklisted, as well as nouveau. My main desktop has large monitors in twinview, my secondary desktop has two TB monitors also in twinview. The media server runs xbmc outputting 720p/1080p content to TVs 24/7. All of them are running up to date QQ and Unity. I get perfect glx (10.000+ on glxgears) and vdpau. My uptime in the server is more than a month (I restart the desktops once a day). 

I have never relied on nouveau or nvidia-current and always used the proprietary installer. When we had the problem with xorg, I downgraded xorg, but everything is up-to-date now and working.

I'm pretty sure it all works, unless I'm actually in an induced coma and this is all a dream.

**EDIT:**  In my opinion, although Jockey had known problems, dropping it for something new and untested is a testimony of the current madness. Serious and risky decisions are being taken by people that are unaware of the OS problems, what works and what does not. Developers are not being fed with testers output or are blatantly disregarding it. Decisions like this, the one about the installer and other we are seeing this cycle are not only offensive to community testers but unintelligent. User experience and the quality of the OS is now in jeopardy. I do not believe the goal of making QQ a release "[focused in Quality]("http://www.markshuttleworth.com/archives/1121")" is being pursued in an effective way. More seriously, the community is apparently being deprecated. Integration, communication and transparency are worst than ever. I agree with everyone that has decided to stay away from this mess. Unfortunately, it makes sense to not support Ubuntu now. 

Regards,
Effenberg

---

### Post by cariboo on 2012-09-05
I'll pipe up here. I'm using nvidia-current-updates from the repositories on a Geforce 210 (218GT) with zero problems.

I've got a three day weekend coming up, so I plan on updating my shop system with a 9400GT to Quantal, so we'll see how it goes.

---

### Post by mc4man on 2012-09-05
I guess time will tell on the reason why add. drivers fails to show anything on nvidia hardware, though obviously we all know nvidia-current is OK & apt-get/synaptic will gladly install.

I'm certainly not smart/knowledgeable  enough to say it's because ubuntu-drivers see abi-11 & halts there, but it sure looks that way here where a simple edit does allow add. drivers to install nvidia*, ect. (as in screen provided & the sky didn't come crashing down.

In the [orig. bug I had]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1044725") there is a debug of u-d-c where it says 
"DEBUG:root:Driver package nvidia-current is incompatible with current X.org server ABI xorg-video-abi-13" which makes sense if it thinks abi-11 is what it is compatible with 

Anyway I would certainly defer to M. Pitts knowledge which is far,far beyond what I could, should, or want to  know...

---

### Post by Elfy on 2012-09-05
Thanks peeps.

I knew I could install the driver from synaptic - was just wondering why it wasn't showing up in additional drivers.

---

### Post by mc4man on 2012-09-05
Well did get on the same page & all squared away, fix committed. I think it's quite understandable that people are a bit stretched atm & may miss a thing or so, ect.

---

### Post by mips on 2012-09-07
> **cariboo907 said:**
> 
I've got a three day weekend coming up, so I plan on updating my shop system with a 9400GT to Quantal, so we'll see how it goes.

Should be fine as it works with my 9600GT ;)

---

### Post by dangmc on 2012-09-10
I installed Ubuntu 12.10-x86_64 beta 1 last Friday, after doing all the updates I installed Nvidia-current (304.43). I haven't so far experienced any of the problems which affected 12.04. I installed Oracle Java 8, Skype, quite a few multimedia apps, etc. So far, everything just works, no installation errors, crashes. Much faster that 12.04, video, sound, web sites using Java greatly improved. No flash video problems.


Asus P7P55D-E motherboard
Intel I5_750 Processor
Ripjaws dual channel ram: 8gb 1600 (4x2gb)
Nvidia 9800GT graphics card
Seasonic 650w. 'gold' power supply
Western Digital 1tb. 'Caviar' hdd x2
Antec P180 case

Triple boot: Ubuntu 12.04-x86_64 and Windows 7 Professional share sda, Ubuntu 12.10-x86_64 on sdb.

I think this distro is going to be everything Precise is not: well planned, just works, few issues. I should mention that bootloader now just finds all systems available with no tweaking. The only problem I had was artifacts completely obscuring desktop upon booting dvd. I tried reburning; no luck  so iso needs to be reworked. My solution to this was to start clicking mouse haphazardly and hit enter until finally booted to 'try Ubuntu'. After that I was able to finish install without further problems.

---

### Post by mips on 2012-09-11
> **dangmc said:**
> 
The only problem I had was artifacts completely obscuring desktop upon booting dvd. I tried reburning; no luck  so iso needs to be reworked. My solution to this was to start clicking mouse haphazardly and hit enter until finally booted to 'try Ubuntu'. After that I was able to finish install without further problems.

Try booting it again with the "nomodeset" option and let us know if it makes a difference.

---

### Post by dangmc on 2012-09-11
> **mips said:**
> Try booting it again with the "nomodeset" option and let us know if it makes a difference.

Sorry, I through it away.

---

