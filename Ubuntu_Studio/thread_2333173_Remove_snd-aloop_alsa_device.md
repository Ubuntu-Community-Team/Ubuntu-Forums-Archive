---
title: "Remove snd-aloop alsa device?"
date: 2016-08-07
forum: Ubuntu Studio
---

### Post by jonas-thornvall on 2016-08-07
I thought i should be clever and install packages from kxstudio into my working ubuntu and get synths plugins and lowlatency drivers, however it did add a virtual soundcard snd-aloop, and it also load and start jackdbus by default, which i really don't like i prefer pulseaudio when surfing internet and listen to music.

The snd-aloop device was set to default alsa device 0 and it crash pulseaudio "manager", impossible to connect.
How can i remove the virtual audio device make my audiocard default alsa so pulse audio can connect again?

Best regards Jonas Thörnvall

---

### Post by jonas-thornvall on 2016-08-07
Since pulse-audio never connect, i can not even switch device is there a file for what alsa-card pulse audio connect to that i can edit?

---

### Post by marseille2 on 2016-08-07
What packages did you install?

Using snd-aloop ([LOOPBACK]("http://alsa.opensrc.org/Jack_and_Loopback_device_as_Alsa-to-Jack_bridge#The_ALSA_Loopback_.27Sound_card.27")) will let you turn off pulseaudio and just use ALSA. But to make it work... the kernel has be set up to use it. I doubt that UbuntuStudio's kernel has aloop ready to use out of the box. I'm on 14.04 and had to set it myself. 

If you want **to use pulseaudio with Jackd** (to surf and record at the same time) ... you need to install the [modules]("http://askubuntu.com/questions/572120/how-to-use-jack-and-pulseaudio-alsa-at-the-same-time-on-the-same-audio-device") -- [COLOR=#333333][FONT=Ubuntu] **module-jack-sink** and **module-jack-source** -- [/FONT][/COLOR]from the Ubuntu repositories (there's no difference between the one in Ubuntu and the one in KX-Studio... and when it comes to the packagemanager, be careful so that you don't break your system).

And last... this is just a tip... consider installing "Cadence" from the KX-Studio repositories. It will allow you to choose which "bridge" you want to use, i.e. -- snd-aloop; pulseaudio; etc...

---

### Post by jonas-thornvall on 2016-08-07
When i open alsamixer gui it show the loopback device i suspect that is because the loopback is listed as hw 0 in alsamixer then the soundcard as 1. 
I suspect that pulseaudio try to connect to the default alsadevice that in this case seem to be loopback device and that is the cause of the fail, it worked perfectly before i installed the kx packages. 

I beleive it may have been some package for wine that introduced the loopback thingy because it was not there when pulseaudio worked, jackd did also work but i had to start it from qjackctl or a daw and it then took over the control of alsa from pulseaudio. 

How can i either get rid of the loopback it wasn't there before or howto tell Alsa that device 1 is default not device 0, because device 0 is the dummy.

---

### Post by marseille2 on 2016-08-07
First see where your card(s) is... (if loopback is working it'll show up, too)... to see what's going on.

For playback:

```
$ aplay -l
```

For recording:

```
$ arecord -l
```

---

### Post by jonas-thornvall on 2016-08-08
It is a intel HDMI device that's why 7 channels i suspect.
But as i said i do not think that it was there before, jackd is no problem because in cadense i can chose output port. But pulseaudio can not connect to the loopback "i suspect" and even if it could it would not be correct?

Could it be wineasio that installed the virtual device?




kort 0: Loopback [Loopback], enhet 0: Loopback PCM [Loopback PCM]
  Underordnade enheter: 8/8
  Underordnad enhet nr. 0: subdevice #0
  Underordnad enhet nr. 1: subdevice #1
  Underordnad enhet nr. 2: subdevice #2
  Underordnad enhet nr. 3: subdevice #3
  Underordnad enhet nr. 4: subdevice #4
  Underordnad enhet nr. 5: subdevice #5
  Underordnad enhet nr. 6: subdevice #6
  Underordnad enhet nr. 7: subdevice #7
kort 0: Loopback [Loopback], enhet 1: Loopback PCM [Loopback PCM]
  Underordnade enheter: 8/8
  Underordnad enhet nr. 0: subdevice #0
  Underordnad enhet nr. 1: subdevice #1
  Underordnad enhet nr. 2: subdevice #2
  Underordnad enhet nr. 3: subdevice #3
  Underordnad enhet nr. 4: subdevice #4
  Underordnad enhet nr. 5: subdevice #5
  Underordnad enhet nr. 6: subdevice #6
  Underordnad enhet nr. 7: subdevice #7

---

### Post by jonas-thornvall on 2016-08-08
Things gone from bad to worse the intelHDMI device 1 that originally could be seen below the loopback device 0 in alsamixer is no longer there i guess that means that the intelHDMI module? somehow been let out from the kernel, otherwise it would been listed?

I tried remove alsa-base, alsa-utils and pulseaudio and reinstalled it still not there, i suspect my Intel compute-stick may use a none supported alsadriver that i got with linuxium but how and why removed i got no idea, maybe i should run the linuxium script to reinstall it.

---

### Post by jonas-thornvall on 2016-08-08
After reinstalling the linuxium script the intelHDMI device/module is now available as soundcard 1 in alsamixer but soundcard 0 is still loopback.
And i guess i have no problem using jackd, or qjackctl reaching the intelHDMI when i need the drivers in DAW's or soundapplication.

And i still can not get pulseaudio connect to card sink? and it is probably because it do not connect to the intelHDMI but to Loopback device. And i guess pulseaudio needed to  get sound when running none jackd application, example i have no sound surfing firefox.

So could please someone tell me howto prevent the loopback module from loading as a alsadriver or howto remove it, because then i suspect that pulseaudio will connect to intelHDMI again?
Now intelHDMI liste aplay -l

**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: Loopback [Loopback], enhet 0: Loopback PCM [Loopback PCM]
  Underordnade enheter: 7/8
  Underordnad enhet nr. 0: subdevice #0
  Underordnad enhet nr. 1: subdevice #1
  Underordnad enhet nr. 2: subdevice #2
  Underordnad enhet nr. 3: subdevice #3
  Underordnad enhet nr. 4: subdevice #4
  Underordnad enhet nr. 5: subdevice #5
  Underordnad enhet nr. 6: subdevice #6
  Underordnad enhet nr. 7: subdevice #7
kort 0: Loopback [Loopback], enhet 1: Loopback PCM [Loopback PCM]
  Underordnade enheter: 8/8
  Underordnad enhet nr. 0: subdevice #0
  Underordnad enhet nr. 1: subdevice #1
  Underordnad enhet nr. 2: subdevice #2
  Underordnad enhet nr. 3: subdevice #3
  Underordnad enhet nr. 4: subdevice #4
  Underordnad enhet nr. 5: subdevice #5
  Underordnad enhet nr. 6: subdevice #6
  Underordnad enhet nr. 7: subdevice #7
kort 1: IntelHDMI [IntelHDMI], enhet 0: IntelHDMI [IntelHDMI]
  Underordnade enheter: 0/1
  Underordnad enhet nr. 0: subdevice #0

I have a fresh installed partition on the stick this is how it was configfured when pulseaudio worked, how can i get it back and remove loopback surely someone knows?

**** List of PLAYBACK Hardware Devices ****
card 0: IntelHDMI [IntelHDMI], device 0: IntelHDMI [IntelHDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

### Post by jonas-thornvall on 2016-08-12
alsactl restore -P

Thank you for nothing

---

### Post by wildmanne39 on 2016-08-12
Thanks for posting the solution and Your Welcome!

---

