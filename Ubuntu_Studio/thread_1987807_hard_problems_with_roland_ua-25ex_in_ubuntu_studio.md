---
title: "hard problems with roland ua-25ex in ubuntu studio 12.04"
date: 2012-05-26
forum: Ubuntu Studio
---

### Post by Carlosll on 2012-05-26
Hello

I'm  desperate. I have bought a roland edirol ua-25ex the past year. yes 201, august.

I have broken 5 or more distros of ubuntu studio and tango studio without even make it sound.

I have read tons of forums and tips. I can't make it work in ardour and the jack... xruns and worst. Never sound.

what can I say? Is there any documentation or bible about ubuntu studio? because, I don't know if I have to set up the limits.conf to audio, install the realtime kernell, If it's better to install the 32bits distro, how to really understand the setup of jack and it's conecctions, If alsa really support the ua-25ex (alsa don't show neither input or outputs), and more.

being more specific: how do I set the parameters in jack?

I have a toshiba satellite 650 (64bits, intel core i5, 4 Gb ram). ubuntu studio 12.04 64bits

Please help me

thank you

---

### Post by jejeman on 2012-05-26
Limits are already set. Lowlatency kernel is already installed.
Give us output from
```
aplay -l
```

---

### Post by Carlosll on 2012-05-27
thank you very much

here it's the ouptut of

 > aplay -l
**** Lista de PLAYBACK dispositivos hardware ****
tarjeta 0: Intel [HDA Intel], dispositivo 0: CONEXANT Analog [CONEXANT Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: HDMI [HDA ATI HDMI], dispositivo 3: HDMI 0 [HDMI 0]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 2: UA25EX [UA-25EX], dispositivo 0: USB Audio [USB Audio]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0


I'm sorry because the output is in spanish.  thank you.

---

### Post by BcRich on 2012-05-27
my apologies for cutting in on this discussion, but I have a similar set-up i.e. three sound sources one onboard my motherboard, another from my ATI/AMD card's HDMI output and my actual external sound device (USB Lexicon Omega).
Carlosll, if all you want is to use the ua-25ex I'd recommend disabling the other devices.
1)I disabled my onboard sound through BIOS (most motherboards have this option, you'll have to look through your motherboards manual for instructions)
2)The easiest way to disable the sound from HDMI output, is to click on the speaker icon in the panel that is installed with ubuntu 12.04 by default, choose sound preferences, go to the hardware tab and you should see your HD-Audio device located there. Simply select it and choose Off as it's profile.
You should also check that your ua-25ex is the device selected in the output tab of the same dialogue box.

---

### Post by jejeman on 2012-05-27
Card is recognized. Let's see if modules are loaded
```
lsmod | grep snd
```

---

### Post by Carlosll on 2012-05-29
Here it is the ouput of lsmod | grep snd
> 
snd_usb_audio         102702  2 
snd_usbmidi_lib        23660  1 snd_usb_audio
snd_hda_codec_hdmi     31064  1 
snd_hda_codec_conexant    57888  1 
snd_hda_intel          30717  6 
snd_hda_codec          99443  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              17255  2 snd_usb_audio,snd_hda_codec
snd_pcm                84403  4 snd_usb_audio,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           12848  0 
snd_rawmidi            27093  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     13316  1 snd_seq_midi
snd_seq                57369  2 snd_seq_midi,snd_seq_midi_event
snd_timer              27226  2 snd_pcm,snd_seq
snd_seq_device         13175  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    65336  28 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              13070  1 snd
snd_page_alloc         17110  2 snd_hda_intel,snd_pcm

thank you jejeman

and in response to BcRich:

The motherboard of this laptop don't have the option to disable the soundcard in the Bios. I'll try to turn it of in the sound preference as you told me.  

it seems to record something but in the moment I want to hear the sound Ardour get collapse and the jack show this message:
> 
 p, li { white-space: pre-wrap; }  Tue May 29 14:49:10 2012: [1m[31mERROR: ALSA: prepare error for playback on "hw:2" (Broken pipe)[0m
 Tue May 29 14:49:10 2012: [1m[31mERROR: JackAudioDriver::ProcessAsync: read error, stopping...[0m


I don't know what is wrong, the conections, the parameters of the jack or what.

the parameters in jack are:

Frames: 64

frequency: the same at the roland ua-25ex

and the buffer is: 3

the ua-25ex it's selected in the interface and the driver it's ALSA.

thank you BcRich

---

### Post by jejeman on 2012-05-29
The modules are loaded too, so it's okay hardware wise.

---

### Post by BcRich on 2012-05-30
hi Carlosll
have u tried doubling frames/period and dropping sample rate to 44100Hz, might help with counteracting xruns (you mentioned in first post)?
As to why Ardour is crashing when you hit play (if i understand your post correctly) I'm a bit stumped. sorry.
Are you able to get sound from other programs like audacious (or something like that)?

---

### Post by Carlosll on 2012-05-31
Hello!!!

Thanks a lot!!!

The audiocard is working!!! with ardour!!!

I am very happy!! thank you!!! :guitar:

So, what was it? I turn off the HD-Audio off in the sound configuration/ hardware.
Then in response to the tip of Bcrich I put the frames to 128 and that was all!!!

In the other hand, the jack did not start when I put the frequency in 4100, as also the audio card.

I'm having 8 mseg of latency. I don't know if this is acceptable, I'll try to do some recordings to prove it. 8 mseg are nothing, aren't they?

Jejeman and BcRich, you will be as heroes in future songs, I wish both of you have a nice life and happy music sessions. 

I live in Spain and if you someday need something from here or from me you will have it.

Thank you very much!!

PD: so this thread is solved. isn't it? do I have to change the thread to [SOLVED]?

thank you!!!

---

### Post by BcRich on 2012-05-31
[http://www.lyndondaniels.com/2010/learn/music/OSSDAW/03recGuitar.html]("http://www.lyndondaniels.com/2010/learn/music/OSSDAW/03recGuitar.html")> **Carlosll said:**
> Hello!!!

Thanks a lot!!!

The audiocard is working!!! with ardour!!!

I am very happy!! thank you!!! :guitar:

So, what was it? I turn off the HD-Audio off in the sound configuration/ hardware.
Then in response to the tip of Bcrich I put the frames to 128 and that was all!!!

In the other hand, the jack did not start when I put the frequency in 4100, as also the audio card.

I'm having 8 mseg of latency. I don't know if this is acceptable, I'll try to do some recordings to prove it. 8 mseg are nothing, aren't they?

Jejeman and BcRich, you will be as heroes in future songs, I wish both of you have a nice life and happy music sessions. 

I live in Spain and if you someday need something from here or from me you will have it.

Thank you very much!!

PD: so this thread is solved. isn't it? do I have to change the thread to [SOLVED]?

thank you!!!

Hi Carlosll
Great to hear you managed to get it working!:popcorn:
8 ms latency is perfectly acceptable.
If you feel like the problem you where having, has been solved then for sure mark the thread as solved :)

Some shameless plugging, if you r planning on doing some guitar recording I wrote a [tutorial]("http://www.lyndondaniels.com/2010/learn/music/OSSDAW/03recGuitar.html") on setting up a simple rig using ardour, maybe you (or some one else reading this) will find some useful info in it?

---

### Post by jejeman on 2012-06-01
10 ms is maximum. Everything under it is good.
I'm working with ~5 ms.

---

### Post by Carlosll on 2012-06-01
Thank you very much BcRich!

I'll read it for sure!! I will rec my guitar with Ardour!!

*May the Force be with you*!

Thank you jejeman!

May you tell me how do you have the jack configurated?

thank you!

*May the Force be with you*!

---

### Post by jejeman on 2012-06-01
Mainly, I use for internal card
```
/usr/bin/jackd -dalsa -dhw:0 -r48000 -p128 -n2 -Xseq -i2 -o2
```
It gives 5.33 ms latency.

For firewire card I use
```
/usr/bin/jackd -dfirewire -r48000 -p64 -n3 -i4 -o2
```
which gives 4 ms.

---

### Post by mjhouska on 2012-06-02
can you translate  that for qjack setup?

---

