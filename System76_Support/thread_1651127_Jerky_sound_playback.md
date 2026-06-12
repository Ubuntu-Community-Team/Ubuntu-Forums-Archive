---
title: "Jerky sound playback"
date: 2010-12-22
forum: System76 Support
---

### Post by andrewdied on 2010-12-22
I've found that sound playback is quite jerky in my Ubuntu 10.10 system.  For example, when playing an mp3 with Amarok, I may get 15 seconds or so of good quality playback, but then the music will reverse and fast-forward for a bit.  I dual-boot the hardware with Windows XP and playback is fine there.

I loaded up the mediabuntu repositories today, and made sure I had the 64 bit codecs installed, non-free, and that sort of thing.  It looks like I'd already had the codecs in, even if the mediabuntu repositories disappeared after my upgrade from 10.04.

My laptop is a Serval Performance serp4, running System76 driver 2.5.7.  If there's any other version or setup information that would be helpful to diagnose the issue just let me know.

---

### Post by isantop on 2010-12-22
Did this issue start when you upgraded to 10.10, or was it fine for a while after the upgrade?

---

### Post by andrewdied on 2010-12-22
I had it for a while in 10.04, and have seen the behavior on and off through several releases.  It's one of those things that "hurt when I did it" so I mostly have avoided sound, I think.

It's unclear to me what specific sound system I'm using, such as ALSA or PulseAudio.  System > Administration doesn't seem to have anything for sound, and System > Preferences just has "Sound", but seems more like where I pick what "beep" sounds like.

From some notes I made it looks like this was the last thing I did, back in 10.04:

20 AUG 2010
Not sure if this will be necessary, but this may fix choppy sound:
[http://forums.virtualbox.org/viewtopic.php?f=3&t=18308](http://forums.virtualbox.org/viewtopic.php?f=3&t=18308)
The PulseAudio sound server has been rewritten to use timer-based audio scheduling instead of the traditional interrupt-driven approach. Timer-based scheduling may expose issues in some Alsa drivers. To turn timer-based scheduling off, replace the line:
load-module module-hal-detect
in /etc/pulse/system.pa by:
load-module module-hal-detect tsched=0

---

### Post by isantop on 2010-12-22
You should be on Pulseaudio, so that may fix it. 

Also, was an upgrade to 10.10, or a fresh install? Try the sound from a LiveCD and see if that help the issue.

---

### Post by andrewdied on 2010-12-23
> **isantop said:**
> You should be on Pulseaudio, so that may fix it. 
How do I verify that, or is Pulseaudio the only choice in 10.10?
> 
Also, was an upgrade to 10.10, or a fresh install? Try the sound from a LiveCD and see if that help the issue.

It was an upgrade.  I've had the same issue on fresh installs of earlier versions, though.  I'll try a LiveCD and let you know how it goes.

---

### Post by andrewdied on 2010-12-27
> **isantop said:**
>   Also, was an upgrade to 10.10, or a fresh install? Try the sound from a LiveCD and see if that help the issue.

Ok, I was finally able to try a 10.10 LiveCD.  (What a rotten pain in the neck to set up mp3 playback, and it never quite worked, anyway.)  I was able to try some ogg vorbis files, and they also skipped.  For those it was like a record player skipping -- it'd stay at 5 seconds play for a while and kept wrapping the last second, give or take.

---

### Post by andrewdied on 2010-12-28
Update: KDE does not have the sound issue Gnome has.

I logged into KDE instead of the Gnome desktop, and loaded the same mp3 file I've been testing with into Amarok, which is the program I've been testing with.  It plays beautifully.  EDIT: XFCE also has the same issue as Gnome, but it took a few minutes to kick in.

KDE says it's using "Internal Audio Analog Stereo" in System Settings > Sound and Video Configuration > Phonon > Audio Output > Music.  When I went there, it wanted to permanently remove "HDA Intel, ALC268 Analog".  

How can I compare what devices KDE is using, vice Gnome?

---

