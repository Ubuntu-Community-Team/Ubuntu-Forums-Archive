---
title: "HDA Intel + Alsa -- Distorted audio"
date: 2010-01-06
forum: Ubuntu Studio
---

### Post by Vixus on 2010-01-06
Hi,

NB: Using the RT kernel, laptop, hda intel driver.
The distortion in question sounds like dropouts rather than spikes or added noise.

During my trials with a Creative X-Fi card I tried switching my Ubuntu system to OSS following this guide:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

After decided it wasn't worth it (the card didn't work and ALSA seemed to recognise it anyway) I tried switching back to ALSA following this:
[http://ubuntuforums.org/showpost.php?p=5539687&postcount=331](http://ubuntuforums.org/showpost.php?p=5539687&postcount=331)

At first everything appeared OK, such as flash audio but then when I tried running any audio apps using ALSA drivers (LMMS, Zasfx, Jack) and the audio output was very distorted and even an ascending series of notes could not be properly discerned.

I have my sound card properly set up, with correct entries in /etc/modprobe.d/alsa-base.conf (checked using my other xubuntu on the dual-boot).

What's up with this? Have I done something wrong reverting back to ALSA? I don't want  to perform a complete system reinstall. :|

Cheers!

---

### Post by Vixus on 2010-01-06
OK, I just had to post this really weird behaviour.

I recorded some key mashing from zasfx into qtractor (via jack) and then opened the resulting clip in audacity...

Audacity plays smooth, undistorted zasfx output! What??
So using zasfx or LMMS directly through ALSA (or rather zasfx uses OSS emulated by ALSA) gives distorted output but recording zasfx via jack and then opening the recorded file in audacity (ALSA) gives clean sound?

Weird.

---

### Post by sgx on 2010-01-07
> **Vixus said:**
> OK, I just had to post this really weird behaviour.

I recorded some key mashing from zasfx into qtractor (via jack) and then opened the resulting clip in audacity...

Audacity plays smooth, undistorted zasfx output! What??
So using zasfx or LMMS directly through ALSA (or rather zasfx uses OSS emulated by ALSA) gives distorted output but recording zasfx via jack and then opening the recorded file in audacity (ALSA) gives clean sound?

Weird.
Hi, in the long run, which should begin in about 15 minutes ;) , its nearly crucial to have a separate /home partition, so your personal configs, eyecandy, and data can be preserved during a reinstall, by choosing to reformat 
/ partition, but not /home partition. 

In the meantime, there should be a command

alsactl, and maybe a script to run it, alsaconf

sudo alsaconf will open a dialogue to choose a soundcard and allow alsa to
configure it. You might install aoss first, as it may help keep subtle differences between alsa and oss in order.
The following may be redundant... but useful for recording


Start qjackctl, click setup in the gui, on the right side, halfway down, are
Input Device / Output Device, click the widgets shaped like >

These will reveal what sound devices are seen by your system.
Select your soundcard.

To record, you can install and use timemachine, a one-big-button recording app that will be listed in qjackctl when you run the command

timemachine

or start it from its icon.

In the qjackctl audio tab, connect timemachine on the right side, to system (your soundcard line-in) on the left side. Place a radio or similar soundsource by your mic for a constant signal, you'll see it monitored in the timemachine interface when the right connections occur. Take notes/pics as desired. You can also open zynaddsubfx, hydrogen, or other software instrument to test recording.

 There will be three tabs in qjackctl, audio, midi, and alsa. The soundcard and timemachine in the audio tab should be connected.
For a synth, start zynaddsubfx. In the alsa tab, zyn will be on the right, your soundcard midi on the left. Connect these, then, back in the audio tab, zyn is on the left side, connect it to both system, and timemachine on the right side. Press the ** button on zyn to open its keyboard, and play some sounds, you'll see
 activity on the timemachine meters when properly connected.

Follow that routine for each linux instrument, like the hydrogen drum machine.

To record, press the green button in timemachine, it all goes orange while recording. Press it again to stop recording.

Your recording will be a high resolution wave file, looking similar to this:

tm-2010-01-01T00:35:15.w64

You can use 'import audio' in Audacity to load, edit, and convert this file to .wav, mp3 as desired.

Cheers

---

