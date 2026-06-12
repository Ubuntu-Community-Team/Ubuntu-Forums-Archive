---
title: "QJackCtl NVidia HDMI full surround sound"
date: 2014-06-02
forum: Ubuntu Studio
---

### Post by gboer01 on 2014-06-02
I have solved a problem connecting QjackCtl to my Home Cinema 5.1 surround box via HDMI.
The box is connected via a HDMI cable with my NVidia video card. 
My CPU is an Intel i5 760 (quad core), a MIDI USB port (brand doesn't show) and a NVidia GTS 450 video card (GF106 chipset) with the proprietary recommended driver NVidia-331.
I'm running Mint17 (Cinnamon), based on Ubuntu 14.04, but I also tried Ubuntu Studio 14.04, as far as I can tell there is little
difference in sound set up. However one important difference is the lowlatency kernel in Ubuntu Studio which I will come 
back to later in this article.


In PulseAudio (the standard audio system) all went well, I was able to play ac3 5.1 files on all 6 speakers with the Banshee media player.


But in QJackCtl (alsa sound system in this case), no matter what settings I tried in Settings: no sound.
Then I tried all sorts of options in /etc/modprobe.d/alsa-base.conf, like:
options snd-hda-intel <many combinations>
But again absolute silence.


My Gnome-alsa-mixer did show my NVidia sound card on all 4 digital S/PDIF chanels as unmuted, so that should be ok.
BTW: Some people might find it strange that there are no volume sliders showing, but this is as it is. The digital
signal is transported over the HDMI interface as it comes in and no mixing can be done (this is different in PulseAudio,
where mixing can be done).


First of all make sure that the Home Cinema set is turned on with input HDMI, BEFORE you start up Linux, else only stereo sound will be heard, and you cannot change to 5.1 sound.
Secondly, do realize that PulseAudio is muted as soon as you start the QJackCtl.


There is only one configuration to be done in QJackCtl: Options tab in Setup...: the addition of a script that plugs in alsa_out into the Audio Connections bay.


To make this script we have to know which audio device has to be set in alsa_out, do this by starting the terminal and type:
aplay -l
This gives you a list of audio devices, in my case:
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: MID [HDA Intel MID], device 0: VT1718S Analog [VT1718S Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 2: VT1718S Alt Analog [VT1718S Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: MID [HDA Intel MID], device 3: VT1718S Digital [VT1718S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


We are interested in the NVidia devices. Alsa shows devices in this way: hw:<card number>,<device number>
So we have 4 devices here:
hw:1,3
hw:1,7
hw:1,8
hw:1,9


Now in order to know which device we need to use we do a little test. In a terminal execute the following:
speaker-test -D hw:1,3 -c 6
Do this for all 4 devices until you hear sound (pink noise) on 6 channels (given by option -c 6).
In my case this was hw:1,7
This device hw:1,7 can play up to 8 channels, so if you have a 7.1 home cinema, set -c 8.


Now to make QjackCtl aware of this sound device we need to configure a script which, in my case, contains one line:
alsa_out -j HDMI_NVidia -d hw:1,7 -c 6 -p 256 -n 2 -r 48000 &
In which the -j sets the name in the QjackCtl audio writable clients bay, -d the alsa device name, -c nr of chanels,
-p Frames/period, -n Periods/buffer and -r Sample Rate.
So with gedit make a script named ~/bin/hdmi_NVidia with this line and make it executable (chmod a+rx ~/bin/hdmi_NVidia).
The next step is to set this script in the QjackCtl Setup... Options tab: Execute script after Startup: ~/bin/hdmi_NVidia
This way the alsa_out will be running in the background, connected to jackd. It shows up in the Audio Connections as hdmi_NVidia with 6 speakers.
It will be automatically closed when stopping QjackCtl, giving this sound device back to PulseAudio.


Now you will find, in case running the standard generic kernel, a lot of latency errors in the Messages window of QJackCtl given by messages like:
XRUN callback(skipped)
I must admit I haven't heard any noticeble latency in the sound output, but if you do, you might want to experiment with different Frames/period and Periods/buffer settings. 
Another option is to use Ubuntu Studio.
Running the same configuration in Ubuntu Studio with lowlatency kernel, I did not get any latency errors. There is a slight disadvantage in
running the lowlatency when you are using OpenGl in games, it reduces the framerate somewhat (5% or so if I remember correctly).

If you do not wish to run Ubuntu Studio with xfce desktop, then you might consider installing the lowlatency kernel in your current Ubuntu 14.04.

ADDENDUM and CORRECTION on installing lowlatency:
Skip this: !!!$ sudo apt-get install linux-lowlatency linux-headers-lowlatency linux-lowlatency-pae
Skip this: !!!Possibly a good idea to backup /boot/grub/grub.cfg before you do so.
Instead:
Install in the Ubuntu Software Manager: "linux-lowlatency", which installs the latest kernel with include files, image etc. It will also perfectly update the grub.conf, so a backup is not needed (...).
The lowlatency kernel will be started by default when power on.
Once started in lowlatency you will have to run 'aplay -l' again, because the devices may have changed card number. I have no latency errors in QJackCtl anymore.

Also you may want to add another line to the ~/bin/hdmi_NVidia script: 
a2jmidid -e &
You first have to install a2jmidid in the Ubuntu Software Manager.
This will enable the midi ports in the QJackCtl: Connect: Midi tab. This is needed to run applications without Alsa midi control jack (like Ardour3). 
I have read somewhere that connecting midi in the Midi tab has lower latency for midi events as well.
Cheers.

---

