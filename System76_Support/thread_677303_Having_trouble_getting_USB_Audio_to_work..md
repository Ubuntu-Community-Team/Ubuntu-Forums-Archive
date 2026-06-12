---
title: "Having trouble getting USB Audio to work."
date: 2008-01-24
forum: System76 Support
---

### Post by frainbart on 2008-01-24
Hi, I can't seem to get the USB Audio to test right on the control panel: System>Preference>Sound. I have a Gazelle Value (gazv1) running Ubuntu 7.10 with a Plantronics USB Stereo Headset (GameCom Pro 1). I get the "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing." error window.

I am trying to use it with Skype and I followed the how-to on the System76 website but I still can't get my headset to work with Ubuntu. Out of the devices listed on the control panel, only OSS and Autodetect play a sound when I hit the test button; the others give the same error as above. The headphone out and laptop speakers work fine. I don't have a microphone to test the phone in.

```
~$ cat /proc/asound/cards
 0 [ICH6           ]: ICH4 - Intel ICH6
                      Intel ICH6 with ALC655 at irq 23
 1 [Headset        ]: USB-Audio - Plantronics Headset
                      Plantronics Plantronics Headset at usb-0000:00:1d.0-1, full speed
 2 [Modem          ]: ICH-MODEM - Intel ICH6 Modem
                      Intel ICH6 Modem at irq 17
~$ cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 1- 0]: digital audio playback
  5: [ 1- 0]: digital audio capture
  6: [ 1]   : control
  7: [ 0- 4]: digital audio playback
  8: [ 0- 3]: digital audio capture
  9: [ 0- 2]: digital audio capture
 10: [ 0- 1]: digital audio capture
 11: [ 0- 0]: digital audio playback
 12: [ 0- 0]: digital audio capture
 13: [ 0]   : control
 14: [ 2- 0]: digital audio playback
 15: [ 2- 0]: digital audio capture
 16: [ 2]   : control

```

---

### Post by frainbart on 2008-01-24
I had posted on the Skype forums with my problems getting Skype installed. I couldn't get into the options panel for Skype (2.0 beta); it was causing the program to quit. Disabling my bluetooth radio fixed the problem and Skype recognized my USB headset using the .asoundrc file in the System76 How-to. I got the test call to work successfully and I can modify the volume of the headset using the volume control applet. However, II still can't get music or system sounds to play through the headset.

---

### Post by imhavoc on 2008-01-24
frainbart,

I've had great results using my bluetooth headset with Skype, but to play other audio to the headset, I have to set the output device on the command line with mplayer.

I'm having almost the exact same problem with Altec Lansing USB speakers AND Logitech USB headsets.

I've tested on my System76 Daru2 (running Kubuntu 7.10) as well as my desktop (nice box I built myself) (also running Kubuntu 7.10). The problems are the same on both systems. I've tried configuring the sound under Gnome, so it's not a KDE problem. I think we're going to have to push this up a level to the Ubuntu community as it seems to be an Ubuntu problem and not a System76 problem. 

I've read reports that the Altec Lansing XT1 USB speakers work perfectly and seamlessly under Fedora, and that's part of what makes me suspicious that it's an Ubuntu thing and not a System76 thing.

---

### Post by thomasaaron on 2008-01-25
The USB headset configurations that you can make within System > Prefs > Sound work primarily with gnome apps.

To configure them with skype, you have to open skype, click the little gear icon at the bottom, go to 'options' > sound device...

In other words, it has to be configured within skype.

---

