---
title: "Video files causing system crash in 12.04"
date: 2012-03-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by nifty542 on 2012-03-03
Hi, all

I'm guessing I'm posting this in the wrong place, but not sure if I can post in the sticky, or how to.
I tried updating to Precise. All video files- including attempting to play a DVD- cause a system crash. The screen goes blank, and in a few seconds the login screen comes up.

-Processors-
AMD Phenom(tm) II X4 965 Processor		: 800.00MHz (x4)
4Gb DDR3 ram
ATI Radeon HD4250

Hope this is of some help.
Regards
Nifty

---

### Post by oldos2er on 2012-03-03
Moved to Ubuntu +1 (Precise Pangolin).

---

### Post by xAltF4x on 2012-03-04
I'm also getting a crash while trying to play any video file in Ubuntu 12.04 Beta 1. (AMD64) Tried multiple video files of various codecs/containers, and both Totem and VLC. Video Card is an AMD HD 6770. fglrx. The screen goes black, then goes to the login screen.

My dmesg seems to show:
> [47489.575582] type=1400 audit(1330880707.877:26): apparmor="DENIED" operation="open" parent=6251 profile="/usr/lib/telepathy/mission-control-5" name="/usr/share/gvfs/remote-volume-monitors/" pid=6252 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0


I get a copy of that for each crash. I do seem to recall a recent update a day or two ago to apparmor, so maybe its something to do with that?

Will gadly try test anything else out to help.

---

### Post by jfernyhough on 2012-03-04
I'm going to guess you have fglrx installed. Try adding "export LIBVA_DRIVER_NAME=xvba" to your ~/.profile, e.g.:

$ echo "export LIBVA_DRIVER_NAME=xvba" >> ~/.profile

then logging out and back in.

---

### Post by nairias on 2012-03-04
same problem here, i updated 11.10 to beta 1 when it showed up.
all videos just cause a logout, not a system crash.

AMD A4-3400 + 8GB RAM, no additional graphics card or any other expansion cards.

edit: adding "export LIBVA_DRIVER_NAME=xvba" to ~/.profile didnt work

---

### Post by xAltF4x on 2012-03-04
> **jfernyhough said:**
> I'm going to guess you have fglrx installed. Try adding "export LIBVA_DRIVER_NAME=xvba" to your ~/.profile, e.g.:

$ echo "export LIBVA_DRIVER_NAME=xvba" >> ~/.profile

then logging out and back in.

Looks like it's definitely related to fglrx. I added the line to .profile like you suggested, rebooted, and the "crash" (really a logout, I guess?) was still there.

So I removed fglrx through jockey, rebooted, made sure radeon was back through an lsmod. And poof, the problem disappeared. Movies would play again.

Then downloaded the latest AMD fglrx from their website, thinking maybe it was a problem with the version that's in jockey. But no, that one still has the video crash too. 

So a workaround for the moment is just to use radeon. (Which I love using in the first place, but the performance just isn't there for a few tasks) Wonder what's changed in 12.04 to cause this?

---

### Post by kelpdip on 2012-03-04
Go into VLC video settings, turn hw overlay mode off. Videos are still hw accelerated regardless. Obviously only a temp fix.

---

### Post by xAltF4x on 2012-03-06
> **kelpdip said:**
> Go into VLC video settings, turn hw overlay mode off. Videos are still hw accelerated regardless. Obviously only a temp fix.

I can confirm that this works. But like you said, only a workaround.

---

### Post by larrypg on 2012-03-07
Yes it does work for the time being.

---

### Post by kelpdip on 2012-03-07
I suspect fglrx. I believe the normal hw overlay setup is done by
aticonfig --overlay-type=Xv
In this version the only options are =OpenGL and =disable. The opengl switch borked things beyond just xorg.conf when I tried it.

---

### Post by xAltF4x on 2012-03-11
I think that the latest driver from AMD (released on the 7th) fixed this issue. I installed it just now and I can play videos with the VLC HW Overlay mode on. 

Anyone else confirm? (That I'm not just doing something silly)

---

### Post by Bukoptimistas on 2012-03-11
> **xAltF4x said:**
> I think that the latest driver from AMD (released on the 7th) fixed this issue. I installed it just now and I can play videos with the VLC HW Overlay mode on. 

Anyone else confirm? (That I'm not just doing something silly)

I had this problem too. (Upgraded from 11.10 to 12.04 beta) 
Your solution worked! I can now playback video files. thanks ([http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx) AMD Catalyst™ 12.2 Proprietary Linux x86 Display Driver | Revision Number: 12.2 | Release Date | 3/7/2012 )

---

### Post by Linuxisfast on 2012-03-22
I am also surprised at the choice of using an older xvba driver version 0.78 when the newer 0.80 is being used by most other distros, maybe the cause of crash is due to this. I have a dual GPU 6270G2 laptop and face the same issue with post release ATI drivers, I will now give the latest Catalyst 12.2 a try.

---

### Post by damianmann on 2012-04-19
This thread makes my hjead explode. How bout some love for the newbs? Make things a little clearer....step by step

---

### Post by Linuxisfast on 2012-04-19
Very simple, Ubuntu 12.04 is beta and therefore one has to go through this. No issues, latest Catalyst update fixes this error.

---

