---
title: "Ubuntu Studio and MicroKorg synthesizer"
date: 2008-09-22
forum: Ubuntu Studio
---

### Post by yarbs on 2008-09-22
Hello all, I am an extremely new user to Linux. I was very excited for the capabilities of ubuntu studio and I have found myself unable to make the transition into those programs. I have a Korg microkorg synth, and would like to not only use it as a midi controller but use it's 128 programs that are built into it as well as it's ability to manipulate the sounds. I also bought a creative labs sound card which I later found out has no drivers for linux currently. So I really need to do my homework, but I also really need the help of someone more versed in the ways of linux. I am sure everyone gets very tired of newbie posts and perhaps I should have put it elsewhere, but this is a media production specific question and I would really appreciate all the help I can get. To paraphrase:
I have the ubunuto studio packages.
I have a usb-midi connection with my Korg.
I want to record using my Korg as a midi controller as well as use it's built in programs.
I need to install a sound driver for the creative labs Xi-Fi series card, if there is not a stable one then I need to know what sound card to purchase.

Once again, I'm a total newbie to linux my friend from work has set me up with the most recent ubuntu update. I just want to be able to lay down these keyboard tracks. If anyone is willing to help me take this on, my blessings are with you. Feel free to contact me or reply to this thread, and many thanks to these forums for being here.

---

### Post by rayj on 2008-09-24
Hey...I'm a relative newbie as well, although I've been mucking about with various Linux distros since the beginning of the year. I think there are essentially two types of Ubuntu Studio user...those who have long-term experience with computers in general, and those like myself who just jump in from a performer/musician's perspective with little or no background in Linux. I'm of the latter, and a sloppy rocker type at that.

I have a MicroKorg as well. However, I splurged and bought a M-Audio Delta 1010 (which is by far the most expensive component in my system...). I think the real answer here is the formulation of a proper question...

For example, I can:

-record the analog output of my MicroKorg
-record the MIDI output of said
-route the MicroKorg's analog output through my card, and matrix several tracks of it through various effect chains...while controlling the parameters of said effects through my Korg's controls...
-use the Korg to run Linuxsampler/SooperLooper, and drop in whatever samples I choose to record...
-any combination of the above, perhaps with some latency here and there

With my upgrade to 8.04, I haven't been able to think of anything I *couldn't* do...and it's all essentially 'plug-&-play', with qualifiers...like reading a little documentation from time to time and searching forums.

If your soundcard works at all, you shouldn't have a problem being nearly paralyzed by all the options Ardour and Jack provide. My word of advice would be not to worry too much about mucking things up, and simply trying it out. You can always wipe out your drive and reinstall if things get too hosed...

---

### Post by pseudo endeavor on 2008-12-29
Hey Yarbs.

Don't know where you find yourself now. Hopefully producing your first open album, and figuring out how to create your own plug-ins for Ardour. If not, I hope you're at least cube spinnin & with us. 

some [Ubuntu documentation]("https://help.ubuntu.com/community/HowToSeq24Introduction") explains creating a song from the get go. I found it very helpful.

---

### Post by theluddite on 2009-06-21
> For example, I can:

-record the analog output of my MicroKorg
-record the MIDI output of said
-route the MicroKorg's analog output through my card, and matrix several tracks of it through various effect chains...while controlling the parameters of said effects through my Korg's controls...
-use the Korg to run Linuxsampler/SooperLooper, and drop in whatever samples I choose to record...
-any combination of the above, perhaps with some latency here and there


I'd really love to have some help with my Microkorg.  I've got it plugged into a midisport 2x2 and have had zero luck reading the signal with aseqdump, kmidimon, Qsynth, seq24 or Zynaddsubfx.  I've tried the tutorials here:  [http://ubuntuforums.org/showthread.php?t=96506](http://ubuntuforums.org/showthread.php?t=96506) and nothing.  Can someone be more specific on how they're recording midi signals with a microkorg or midisport?

---

### Post by slwx on 2010-11-17
Hi,
is this thread dead? cause i'd like to know what you guys can alld o whit your microkorg, and how you got it working!
thx
Mathi

---

### Post by cchhrriiss121212 on 2010-11-17
> **slwx said:**
> Hi,
is this thread dead? cause i'd like to know what you guys can alld o whit your microkorg, and how you got it working!
thx
Mathi
It is dead. Try starting a new thread and describe what your setup is (soundcard etc), how you intend to connect your microkorg (are you also using a midisport?), what your goals are and anything else relevant.

---

### Post by theluddite on 2010-11-22
> **slwx said:**
> Hi,
is this thread dead? cause i'd like to know what you guys can alld o whit your microkorg, and how you got it working!
thx
Mathi

I'm still subscribed.  My problem turned out to be with the kernel.  After I compiled my own custom realtime kernel, the MicroKorg worked fine with my midisport 2x2.  I realize this is MUCH more work than most people want to do.  

I hate to say it, but I've switched back to Windows for music production.  I found myself spending way too much time debugging software and hardware that either didn't work out of the box or spontaneously broke, which is time I could have been spending actually writing music.  I know this is probably the last thing you want to hear (because I didn't want to hear it while in your shoes) but consider a dual-boot.

---

### Post by slwx on 2010-11-22
well, I'll guess dual boot it is :)

music production & gaming, 2 reasons to stick with microsoft..

thx

---

