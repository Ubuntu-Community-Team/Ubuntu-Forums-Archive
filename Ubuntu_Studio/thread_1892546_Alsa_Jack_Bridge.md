---
title: "Alsa Jack Bridge"
date: 2011-12-08
forum: Ubuntu Studio
---

### Post by mikee55 on 2011-12-08
Hi all, can someone post a link to get my Alsa and Jack bridged, I want to use Mplayer to play a movie through Jack.

Thank :popcorn:you

Mike

---

### Post by jejeman on 2011-12-08
There is no need for any kind of "bridging".
1. start jack
2. start mplayer
3. set mplayer output to jack
4. if needed connect mplayer output to system playback in jack.

---

### Post by mikee55 on 2011-12-10
Hi jejeman, no I tried that, its not showing up in Connect on Jack, not sure why? But there is a link somewhere on this forum that has a bridge.

Cheers Mike

---

### Post by jejeman on 2011-12-11
Maybe you need to start playing video for mplayer to show in jack.
I don't want to install mplayer on this machine, but I've had succesfully playing videos like I've decribed on other machine. When I come to that other machine I will take a look.

---

### Post by mikee55 on 2011-12-11
Hi jejeman, got that happening. The problem I got now, is I want to use Jamin to eq my speakers, like I do with music, but when the next video comes on, it by passes Jamin and I have to re Connect it! Any ideas why?
Thank you
Mike

---

### Post by jejeman on 2011-12-11
It's because mplayer reconnects to jack on each file in play list. Just like vlc, too.

---

### Post by trulan on 2011-12-13
The workaround is to start playback, then hit pause, make your Jack connections, then un-pause.

There have been a few programs (such as the minimalistic audio player Potamus) that handle this in a much more sensible way.  That is, they create Jack ports when the program is started and keep them there until you close it.  Unlike VLC or MPlayer, which remove their Jack ports if you so much as hit 'stop' while playing a file.

There are several possible solutions:
1. Pulse Audio to Jack bridge
This is either in the default repositories or in faltx's ppa, I don't remember which.  I tried this method a few times in its early days and found it quite frustrating.  But it may have improved by now.

2. alsa-to-jack bridge
There are two ways that I know of to do this:
[http://alsa.opensrc.org/Jack_and_Loopback_device_as_Alsa-to-Jack_bridge](http://alsa.opensrc.org/Jack_and_Loopback_device_as_Alsa-to-Jack_bridge)
...which I have set up and have used many times, though I usually keep it disabled to save system resources.  It will route all sounds through Jack always.

[http://linuxhomerecording.blogspot.com/2011/11/jack-alsa-bridge-kit.html](http://linuxhomerecording.blogspot.com/2011/11/jack-alsa-bridge-kit.html)
...which I played with briefly but did not take the time to really get it working.  It claims to be less resource intensive, and it also requires you to select the alsa loopback soundcard for each application you wish to route through Jack.  (That's the part I didn't take the time to figure out.)

Both of these methods make use of the alsa-loopback module, which is not included in default Ubuntu kernels.  So, you'll either need to re-compile your kernel or compile the alsa drivers to be able to use this.    The first link I posted includes instructions for recompiling alsa.

These alsa-to-jack bridges will do exactly what you are looking for.  But getting it all set up is not for the faint of heart.  The Pulse Audio-to-Jack bridge is probably easier if you use Pulse audio (which my production machine does not).  Good luck!

---

### Post by reteo on 2011-12-25
> **trulan said:**
> 
...which I played with briefly but did not take the time to really get it working.  It claims to be less resource intensive, and it also requires you to select the alsa loopback soundcard for each application you wish to route through Jack.  (That's the part I didn't take the time to figure out.)

Actually, you're not using the loopback soundcards directly.  What you use are the "custom" devices created in the .asoundrc file to connect to a specific loopback sub-device.  I will add that this method does not work for all programs, just those that will accept a custom ALSA device as a soundcard.

This will not work for those using a drop-down showing only the devices in /proc/asound/cards that are detected at startup.  The number of applications that do this are getting distressingly large.   I am attempting to find a way to add those custom devices to the card list, so they can be used by all Alsa-supported apps.

---

