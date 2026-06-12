---
title: "UStudio on Thinkpad T42 - Am I nuts?"
date: 2009-11-20
forum: Ubuntu Studio
---

### Post by Copland Audio on 2009-11-20
I'd like to repurpose an old Thinkpad T42 as a mobile recording rig.  1.5 Gb of RAM, Pentium M Processor.  I have a basic Tascam US-122 as a USB interface.  My question is - am I setting myself up for trouble to think I can do this?  I'd rather not fight with it, but would love to hear from those (if any) who have done something similar.  Also, if feasable, should I stick with the 32 bit version?

---

### Post by tgalati4 on 2009-11-20
T42's would make a decent recording rig.  The older disk drive might not be up for it.  I just replaced mine in my T43p with a WD320 blue scorpio--The largest you can get for PATA/IDE.  You certainly need space for recording.  You can use USB drives as well for megaspace.

Make sure you get the real-time kernel working properly and peg the processor speed to max (performance mode) and be sure to use a fan and set it on a milkcrate because it will get toasty.

---

### Post by mango42 on 2009-11-21
What tgalati4 said plus I'm attempting the same thing on a T43. I made a mistake by d/loading UbuntuStudio 8.04 instead of 9.04 (thinking the LTS would be nice...) but I'd forgotten about the issue of WiFi drivers back then, hence no net.

So long as you don't want to record 8 stereo tracks at once, I don't see any major issues really, if you have a decent Firewire 400 i/f in yer Express slot (Belkin & Lindy _Firewire only_ cards seem to work okay), a compatible audio i/f (see ALSA project & FFADO sites) and a separate USB midi interface.

---

### Post by Copland Audio on 2009-11-21
So what I'm hearing is it's doable...I was thinking of getting Ubuntu Studio 9.10 (should I just stick with 32bit?  I'm not anxious to introduce any more potential problems).  As for kernel tweaks and processor settings - could you go into a little more detail there?  I follow terminal instructions well, and would love to know any other thinkpad specific tweaks issues I'll need to take into account (i.e. should I install the tp_smapi module ? or stick with default Ubuntu Studio settings?)

The audio/MIDI interface I'm using is a Tascam US-122 USB interface(any specific instructions there would be helpful also), and was thinking of just using an external usb drive, but it sounds like getting a better internal drive would be the right way to go (and I can just transfer to external storage for space).  I have a Startech CB1394 firewire adapter card...should I have that plugged in when I install just to keep my firewire options open, or again, am I just asking for more intense work and frustration?

I'm not looking to do major production work, just some sequencing, and no more than 2 tracks recording at one time.  I appreciate all the comments!  Thanks!

---

### Post by mango42 on 2009-11-24
I don't have sufficient knowledge to guide you - it would be a case of the blind leading the blind. I haven't even got this T43 machine to resume or selectively switch off the trackpad yet! Maybe tp_smapi could help me too, but isn't that for >=T60 series? 

However, I don't think a 64 bit system will offer any benefits to our 'ancient' 32 bit boxes ;-)

Re: your Tascam unit, you might find this page useful (this depth level makes me go cross-eyed ;-)

[http://alsa.opensrc.org/index.php/Tascam_US-122](http://alsa.opensrc.org/index.php/Tascam_US-122)

Personally, I'm saving usb for MIDI, backup disc etc and using a Linux-friendly Firewire express card for audio as probably being more glitch-free. There do seem to be some gotchas but present contributors like Stochastic, AutoStatic & trulan are certainly helping to smooth the path. Plenty of others have contributed great 'howto' articles...

Good luck and apologies for not spotting your response sooner.

---

