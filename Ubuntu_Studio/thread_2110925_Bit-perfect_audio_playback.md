---
title: "Bit-perfect audio playback?"
date: 2013-01-31
forum: Ubuntu Studio
---

### Post by detlev24 on 2013-01-31
Hi,

I'm trying to get bit-perfect audio playback on my system using Ubuntu Studio 12.04 and XBMC 12.0 (with its new HD [_AudioEngine_]("http://wiki.xbmc.org/index.php?title=AudioEngine")).

My sound card is an [_ASUS Xonar Essence STX_]("http://www.asus.com/Sound_Cards_and_DigitaltoAnalog_Converters/Xonar_Essence_STX") ([_AV100_]("http://www.alsa-project.org/main/index.php/Matrix:Module-virtuoso") chipset).


If I'm not wrong Ubuntu Studio runs - after a fresh installation - completely via PulseAudio and this in not enabling bit-perfect output. I read that ALSA should be the solution so:

**1.** Is it enough to run **sudo apt-get purge pulseaudio && sudo apt-get autoremove pulseaudio**?

**2.** Does ALSA need some extra files that have to be installed?

**3.** Which graphical mixer do you recommend for ALSA?


Something else: can Ubuntu Studio be installed without all the packages I don't need as *ubuntustudio-graphics*, *ubuntustudio-video*?

Thanks!

---

### Post by jejeman on 2013-01-31
1. No need. Just turn it off.
2. I don't think so
4. Only via mini.iso.

---

### Post by ttoine on 2013-01-31
1 - [https://help.ubuntu.com/community/UbuntuStudioPreparation#Disabling_PulseAudio](https://help.ubuntu.com/community/UbuntuStudioPreparation#Disabling_PulseAudio)

2 - depending of the audio chipset of your soundcard, you may need some extra package like alsa-tools, alsa-firmware-loaders and alsa-tools-gui.

3 - try Gnome Alsa Mixer, it is one of the most complete.

---

### Post by detlev24 on 2013-02-05
> **ttoine said:**
> 1 - [https://help.ubuntu.com/community/UbuntuStudioPreparation#Disabling_PulseAudio](https://help.ubuntu.com/community/UbuntuStudioPreparation#Disabling_PulseAudio)

2 - depending of the audio chipset of your soundcard, you may need some extra package like alsa-tools, alsa-firmware-loaders and alsa-tools-gui.

3 - try Gnome Alsa Mixer, it is one of the most complete.
Thanks a lot!


**1.** After the system switched to ALSA there was no sound but that solved it:
[B]sudo mv /var/lib/alsa/asound.state /root/
sudo mount -t tmpfs none /var/lib/alsa
[/B]
**2.** Also everything seemed to work out of the box I did install the additional [_ALSA packages_]("https://help.ubuntu.com/community/UbuntuStudioPreparation#Specific_supported_hardware").

**3.** After 2. there already was an ALSA graphical mixer on board.

(4.) I chose to install Ubuntu Server Edition (LTS) and I did perform:
**sudo apt-get install linux-lowlatency ubuntustudio-audio ubuntustudio-desktop xubuntu-restricted-extras**

---

