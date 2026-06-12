---
title: "Intrepid Support! System76 Driver 2.2.7 Released"
date: 2008-10-29
forum: System76 Support
---

### Post by crichell on 2008-10-29
System76 Driver 2.2.7 was just uploaded to our repository. This update adds support for Ubuntu 8.10 Intrepid Ibex on all System76 computers.

Intrepid goes gold tomorrow! Upgrade directions will be available at  [http://knowledge76.com](http://knowledge76.com) once Ubuntu post their official upgrade notes.

Fresh install folks can follow our restore directions at [http://knowledge76.com/index.php/Restoring_Your_System](http://knowledge76.com/index.php/Restoring_Your_System). One important difference is that the System76 Driver no longer installs nVidia's proprietary driver. To install nVidia's driver we recommend using System > Administration > Hardware Drivers. (All systems shipped from the factory still come with nVidia's drivers installed.)

If you experience any hardware bugs please let us know at [https://bugs.launchpad.net/system76](https://bugs.launchpad.net/system76).

For good measure run the following two commands in your terminal to add the System76 repository and System76 repository signing key:

```
sudo wget http://www.planet76.com/sources.list.d/system76.list -O /etc/apt/sources.list.d/system76.list
```

```
wget -q http://planet76.com/repositories/system76_dev.pub -O- | sudo apt-key add - && sudo apt-get update
```

---

### Post by laserline on 2008-10-30
Hi,

What fixes/tweaks does this driver provide the 'daru2' ?
I've installed Intrepid and haven't noticed any issues except the following:
[LIST=1]
[*]Suspend doesn't work
[*]Battery is flakey (using acpi=noirq)
[*]Microphone doesn't work - I can't seem to record sound etc.
[/LIST]


Thanks,
Idan.

---

### Post by thomasaaron on 2008-10-30
It installs the acpi=noirq kernel parameter. This should keep the monitor from being flaky, although it is pretty slow to register.

It also installs a model designation in /etc/modprobe.d/alsa-base that activates the mics.

The mics work fine, but you have to set System > Prefs > Sound to Pulse Audio.

---

### Post by laserline on 2008-10-30
Which one should I set to PulseAudio ?

Thanks.
Idan.

---

### Post by thomasaaron on 2008-10-30
In testing, I set all of them to pulse audio except the last one, which doesn't have a pulse audio option.

---

### Post by TheBuzzSaw on 2008-10-31
I attempted to install the nVidia driver (version 177, I believe), but it just sits at 0% forever; it never downloads. Anyone else having this problem? I'll try it again in a minute. I'm installing system76 stuff right now (just got 8.10 up and running on my Wild Dog).

EDIT -- Nevermind. Even though I canceled it, it seemed to install/activate anyway. I'm slowly catching up to my previous configuration. ^_^

---

### Post by laserline on 2008-10-31
> **thomasaaron said:**
> In testing, I set all of them to pulse audio except the last one, which doesn't have a pulse audio option.

Hi Tom,

I can't get the mic. working.
I've installed a fresh Ubuntu 8.10 64bit.
Installed the 2.2.7 driver. (I checked that the correct lines were edited -- the only driver for 'daru2' is the 'alsa4' )

When to Sound, set all to PulseAudio and the mic. doesn't work.
I tried recording sound with the with 'Sound Recorder'

Can you please post your screenshots of the equilizer

Please note that I was unable to use the mic. in 8.04 -- although it DOES work under Windows.

Thanks,
Idan.

---

### Post by thomasaaron on 2008-10-31
Hi, laserline.

Please shoot me an email on this, and I'll work on it.
support(at)system76(dot)com

---

### Post by Viranh on 2008-10-31
Is there anything specific in it for the serp4? I haven't found anything that doesn't work yet.

---

### Post by Ocean Machine on 2008-11-02
I can confirm that going to PulseAudio got the mic working on my daru2. Cheese still won't recognize the webcam. I'm having problems with suspend also; the computer just turns off.

---

### Post by laserline on 2008-11-03
> **Ocean Machine said:**
> I can confirm that going to PulseAudio got the mic working on my daru2. Cheese still won't recognize the webcam. I'm having problems with suspend also; the computer just turns off.

Can you please state exactly what you did to make it work ?
Mixer settings and all.. ?

Thanks,
Idan.

---

### Post by thomasaaron on 2008-11-03
Cheese is broken in Intrepid.
Suspend has been broken on the DarU2 for some time. We're still trying to figure that one out.

---

### Post by Ocean Machine on 2008-11-03
> **laserline said:**
> Can you please state exactly what you did to make it work ?
Mixer settings and all.. ?

Thanks,
Idan.

All I did was go to Sound and change "Sound Capture" to "PulseAudio Sound Server" on the Devices tab.

Here's my volume mixer...

[IMG]http://i82.photobucket.com/albums/j246/adambargar/Mixer.png[/IMG]

---

