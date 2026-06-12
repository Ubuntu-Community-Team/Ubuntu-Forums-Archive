---
title: "How do I record my own sounds?"
date: 2008-07-18
forum: Ubuntu Studio
---

### Post by klas_katt on 2008-07-18
kubuntu hardy 64bit on an ASUS A8N-E motherboard.

have installed:
alsamixergui
kmix
qjackctl
patchage
rezound
ardour
vlc

I would like to make some music. I am trying rezound and ardour using a microphone and a guitar through an effect processor. From mic input, I use mic boost on (+20 dB) in kmix. I can (not always) hear myself through the stereo speakers. (I don't know what settings to use.) But I cannot record from mic input or line-in. I can patch output from streaming radio in vlc to ardour and put effects on and record. With ardour I can patch the vlc output channels to the input track channels which output are pached into the master channels that are passed on to the system playback channels. It works, mostly.

The input or mic or line-in does not show up in qjackctl and I don't know what the input "channels" are called.
In qjackctl's connect window I can see capture_1 and capture_2 under output > system. There is also playback_1 and playback_2 under input > system. I connect them but nothing can be heard. Well, sometimes...

alsamixergui says I have the RealTek ALC850 rev 0 chip.

This is the output of:
me@puter:~$ arecord --list-devices
**** List of CAPTURE Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 1: Intel ICH - MIC ADC [NVidia CK804 - MIC ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

me@puter:~$ lshw -class sound
WARNING: you should run this program as super-user.
  *-multimedia
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0

Maybe this output is different depending on what sound apps are running. 
Sometimes when I have vlc or amarok running JACK won't start. With JACK running amarok won't play and displays the message: "xine was unable to initialize any audio drivers." Why is that? Why won't all sound show up in JACK?
What is the significance of starting JACK when i have qjackctl running (pressing the play button) and having it stopped? What is the difference between the "connect" and "patchbay" windows? In patchbay only "Midi Through port-0" and "MPU-401 UART" show. 

I want to save a JACK configuration. How?
Should i go with patchage instead?

me@puter:~$ patchage
lash_open_socket: could not connect to host 'localhost', service '14541'
lash_comm_connect_to_server: could not create server connection
lash_init: could not connect to server 'localhost' - disabling LASH
Failed to connect to LASH.  Session management will not occur.
Loading configuration file /home/blablabla/.patchagerc
Unable to load file /home//blablabla/.patchagerc!
Connecting to Jack... could not connect to jack server.
terminate called without an active exception

alsamixergui:
What drawbars are significant? Why are some of them unclickable? What does the lock and the green/white dottted or undotted speakers mean? There are so many combinations.

(Hmm, no code tag button?)

---

### Post by klas_katt on 2008-07-22
***Bumpety-bump-bump***

---

### Post by klas_katt on 2008-07-24
xtra info

me@puter:~$ lsmod | grep snd
snd_mpu401             11304  0
snd_mpu401_uart        11264  1 snd_mpu401
snd_seq_dummy           5764  0
snd_seq_oss            38912  0
snd_intel8x0           40872  0
snd_ac97_codec        123224  1 snd_intel8x0
snd_seq_midi           10688  0
ac97_bus                3840  1 snd_ac97_codec
snd_pcm_oss            47648  0
snd_mixer_oss          20224  1 snd_pcm_oss
snd_rawmidi            29856  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     10112  2 snd_seq_oss,snd_seq_midi
snd_pcm                92168  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq                63232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27912  2 snd_pcm,snd_seq
snd_seq_device         10644  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    70856  13 snd_mpu401,snd_mpu401_uart,snd_seq_dummy,snd_seq_oss,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         13200  2 snd_intel8x0,snd_pcm
soundcore              10400  1 snd

---

### Post by russo.mic on 2008-07-26
Well, neither of those programs actually record, and one doesn't replace the other. 

patchage is for routing signal around your system's hardware and software inputs and outputs.  Jack config is for configuring your audio hardware. 

I recommond ardour for recording.  it's pretty easy to use and pretty powerful.  It's installed if you've got Ubuntu Studio.  when you open it, you'll see it's i/o in patchage, and be able to route an input to a channel in it.

You probably want to invest into a  decient audio interface if you plan on doing any kind of serious recordings.  You'll want a decient pre-amp, and some low latency hardware.  The Presonus Firepod is a great interface for linux use from what I can tell.  I've got 3 of them in a rack and them and ardor is my mobile recording rig.

Good Luck!

Russo

---

### Post by klas_katt on 2008-07-26
again:

*   I have ardour. And rezound. I have used them a bit already.

*   I have no way of recording own sounds/music.

*   I want to connect mic and/or line-in to recording software. 

*   I tried qjackctl for that, many howtos that I've read uses jack to connect audio, isn't jack for that?

*   patchage wont start, it complains about LASH???

...as my post states

I don't want to buy equipment before I can make recording work. Sound quality through the speakers is ok at this stage.

I'm not and never will be a professional musician, but I'd like to do this. Just having a musical "notepad" for ideas would be very useful.

NEW!
I have lash-bin. lash_panel is not as "self explanatory" as [http://lash.nongnu.org/](http://lash.nongnu.org/) thinks. There is only "Open".

Rezound doesn't show up in input/writable clients in qjackctl, only in output.

---

