---
title: "VirtualBox = choppy sound?"
date: 2010-02-20
forum: Virtualisation
---

### Post by altjx on 2010-02-20
I've tried VMware and it totally sucks for Linux for me... Freezes other applications and everything... so I DL'd VirtualBox, everything's PERFECT, minus the choppy sound...

I'm listening to a DVD in Windows 7 in VirtualBox but the sound is pretty choppy... I have 1GB allocated to it (i have 4GB total)
Any solutions?

---

### Post by underquark on 2010-02-20
I get choppy sound on XP startup (almost exactly as the real XP did on my old machine, mind you).  I edit digital TV shows (MPEG-2 to MPEG-2, to JPG etc.) using VideoReDo and find that sound is OK so long as the video window is kept to about half the screen area.  VLC sometimes barfs a bit but, again, better if playback screen size reduced. So, faster machine, reduce the CPU and memory demands and reduce special effects to a minimum and see how you get on.  I use Project-X in ubuntu for "big" stuff but don't have any audio playback at all when it is running.  I can't see that using Win7 inside a VM is the way to go for watching DVDs when there are native ubuntu solutions.

---

### Post by jpl888 on 2010-02-20
I found that sound wasn't great in VirtualBox until I choose the OSS driver in the settings. See attached screen shot.

---

### Post by altjx on 2010-02-20
Thanks =)

---

### Post by tld on 2010-03-02
Thanks jpl888!  Simple solution worked for me too.

---

### Post by jpl888 on 2010-03-02
You're welcome.

---

### Post by jsa13 on 2010-03-07
Choppy audio solved by installing "libsdl1.2debian-pulseaudio"!

You can keep the default pulseaudio setting in the guest machine.

---

### Post by HoneyBadger1 on 2012-03-01
I am running Ubuntu 10.04 as host, with Windows 7 inside Virtual Box.
I have choppy audio too, and when I switched from ASLA to OSS it didn't fix the problem...I lost sound all together. :(

Is there any other way I can fix this?

---

### Post by pdxmusl on 2012-05-05
I've been having choppy audio as well using ubuntu as a host (11.04, 11.10, and 12.04) and any windows operating system as a guest (I've tried 95 all the way through w7).

From what I've been reading, this is a bug in virtual box. Something that's been fixed for Mac users, but hasn't been addressed yet for linux users. You can test this by RDPing into your guest OS and try doing some simple things like... watching a video on youtube or whatever. Most of what I've been reading suggests the audio works mostly fine this way. It may chop bit every once in a while still. For me, using it this way I rarely here audio choppiness. I haven't done anything to the settings for audio. However, this is not the ideal way to use the guest OS and it sort of breaks its use for games.

Virtual box has a bug issue opened for this:
Bug# 6816 
(not sure if I can technically post web links here... my apologies if this doesn't work right).

[https://www.virtualbox.org/ticket/6816](https://www.virtualbox.org/ticket/6816)

---

