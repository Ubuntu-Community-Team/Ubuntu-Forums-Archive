---
title: "No sound with Jack"
date: 2010-06-30
forum: Ubuntu Studio
---

### Post by nick&amp;dad on 2010-06-30
Hi,

(I'm an almost total noob, using Ubuntu 10.04 "upgraded" to Ubuntu Studio)

I can't seem to get any sound with Jack.  Everything's fine until I start Jack, then all the sound cuts out until I quit it.  I've installed the low latency kernel and as far as I know the message window is saying everything's OK.   I've tried all the different interface options on setup - some result in error messages.  I'm using crappy onboard sound.

Thanks

---

### Post by psy-man on 2010-06-30
hi,
 don't worry, this is a common experience:-/
 here is a good place to read about configuring ubuntu-studio and jackd
 [https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)
.

---

### Post by Pablo_F on 2010-06-30
... And jack server only works for jack clients. This means that you must "jackify" the multimedia player if you want sound from it when jack is running.

See: [http://www.linuxmusicians.com/viewtopic.php?f=19&t=2507](http://www.linuxmusicians.com/viewtopic.php?f=19&t=2507)

Cheers! Pablo

---

### Post by nick&amp;dad on 2010-07-01
Hi,

Thanks for these responses.  

I'm getting no sound from JACK, even from JACK-y programs like ZynAddSubFX.

I've been through the documentation you linked to but I can't find the problem.  The connections are showing up fine in the Connection Box, and I've tried various settings in the Setup.

Richard

---

### Post by Pablo_F on 2010-07-01
Hi, 

Please, open a user terminal window (Applications -> Accesories -> Terminal) and, with a working jack setup (so you see "Started" in the display of Jack Control), with the alsa driver, give the output of the following informative commands:

```
cat .jackdrc
cat /proc/asound/cards
aplay -l
```

This is to check:

That you are using the right driver (It must be "alsa" in your case)
That you are using the right interface (or, possibly, what alsa calls "devices").

Cheers! Pablo

---

### Post by nick&amp;dad on 2010-07-01
Here's what it said:  (loads of thanks for your help, btw)

richard@richard-desktop:~$ cat .jackdrc
/usr/bin/jackd -t2000 -dalsa -dhw:0 -r44100 -p512 -n2 -S
richard@richard-desktop:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfbff8000 irq 21
 1 [Cable          ]: USB-Audio - USB Midi Cable
                      USB Midi Cable at usb-0000:00:02.0-8, full speed
richard@richard-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
richard@richard-desktop:~$

---

### Post by nick&amp;dad on 2010-07-01
ps, I don't know if it's relevant, but with Jack running & ZynAddSubFx the Sound Preferences box tells me the "no application is currently playing or recording audio"

---

### Post by Pablo_F on 2010-07-01
No, it is not relevant because the Gnome Sound preferences applet is not jack-aware. In other words, Jack is not integrated into the gnome desktop. 

You use Jack Control, Connections window, to make the virtual connections between jackified apps and the soundcard, which Jack calls "system". Some apps autoconnect to the system playbacks 1 and 2. Usually, these are the front stereo channel.

So to speak, Jack talks with the alsa driver. At this point, you should check at a lower level. Open a terminal and launch:

alsamixer

There are graphical alsamixers too, like gamix, qamix or gnome-alsamixer, but try first with plain CLI alsamixer. By the way, Gnome Sound Preferences is integrated with pulseaudio, another sound server which we are disregarding by the time being (although it is useful in some circumstances, let's focus on jack first).

Use the arrows and "M" to mute/unmute. It could be that some level is very low, muted or maybe you have connected your speakers to a channel that is not system_playback 1 and 2 from the point of view of jack.


You can always enter #ubuntustudio IRC channel on irc.freenode.net and ask for help there. If someone is on and willing to help it is much faster.

Cheers! Pablo

---

### Post by psy-man on 2010-07-01
yes, un-muting the channels in the alsamixer that was my first head scratch, I had forgotten.  [IMG]http://rosegarden.sourceforge.net/tutorial/pixmaps/sound-diagram-master.jpg[/IMG]
Thought this might be useful to those trying to understand how it all fits together.

---

