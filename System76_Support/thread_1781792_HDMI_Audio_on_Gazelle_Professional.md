---
title: "HDMI Audio on Gazelle Professional?"
date: 2011-06-14
forum: System76 Support
---

### Post by GSF1200S on 2011-06-14
I recently setup a System76 Gazelle Professional (p6) for a friend, and verified with one of my monitors that HDMI video works. Unfortunately, I didnt think to try HDMI audio. If the computer is running 11.04, will the HDMI audio work out of the box or will I need to tweak it (I sent it via UPS today, so I will have to walk her through it)? My friend isnt really proficient with Ubuntu yet, and thus id appreciate if you could throw any advice/information out there- shes a teacher who will be using it to show video clips relevant to her subject material. Cheers :)

---

### Post by isantop on 2011-06-14
It won't quite work out of the box, per se, but it is very easy to set it up. Simply plug in the monitor via HDMI, open up the sound preferences item in the volume indicator, then go to the output tab and select the HDMI digital sound device for output. If you aren't getting sound from the speakers on the monitor, then go to the hardware tab, select the HDMI device, then change the setting for "Profile", trying one at a time until the sound comes through.

---

### Post by GSF1200S on 2011-06-14
> **isantop said:**
> It won't quite work out of the box, per se, but it is very easy to set it up. Simply plug in the monitor via HDMI, open up the sound preferences item in the volume indicator, then go to the output tab and select the HDMI digital sound device for output. If you aren't getting sound from the speakers on the monitor, then go to the hardware tab, select the HDMI device, then change the setting for "Profile", trying one at a time until the sound comes through.

Do you happen to know of a way that doesnt include PulseAudio (in other words, using alsa)? I removed it due to Skype (had to do a test call to switch from the internal mic to USB mic/webcam). If not, reinstalling pulseaudio is possible at least- good to hear and thank you very much for the reply! :)

---

### Post by isantop on 2011-06-15
I don't. PulseAudio is very tightly integrated with Ubuntu at this point, and removing it can cause lots of problems in other applications as well. Pluseaudio should work with Skype, so I would reinstall it anyway.

---

### Post by GSF1200S on 2011-06-16
> **isantop said:**
> I don't. PulseAudio is very tightly integrated with Ubuntu at this point, and removing it can cause lots of problems in other applications as well. Pluseaudio should work with Skype, so I would reinstall it anyway.

Thank you for your responses isantop :) I recently helped my friend setup HDMI using BOTH pulseaudio and ALSA, and both work well. I am posting here for others who might be curious as to how its done.

Go into Nvidia X server settings, X server Display Configuration, Detect Displays, click on the disabled display, configure, twinview, clone/whatever config you want, apply.

Pulseaudio: Open VLC media player (what I used), Tools, preferences, audio, and select Pulseaudio output as the output device. Go into pulseaudio volume control, go to the playback tab and select HDMI as the playback device for VLC media player. Then, switch to the configuration tab and go through the profiles just as isantop suggested.

ALSA: Go into Alsamixer or a GUI equivalent (used XFCE's mixer), click on sound card (or F6 to select sound card), select HDA NVIDIA, and then enable the switches (on XFCE's mixer I had to make them visible first) or S/pdif outputs (alsamixer from command line). Youll only have to do this once, then its done forever. Then, open vlc media player, go to audio, output, device, and then select one of the HDA NVIDIA devices (hw 2;7) worked for me). Done.

Thanks isantop for the support :)

---

