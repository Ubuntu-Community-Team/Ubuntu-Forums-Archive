---
title: "sound card problems"
date: 2016-10-06
forum: Ubuntu Studio
---

### Post by boombox2 on 2016-10-06
hello all,
I have put together a PC from components found in a scrapyard, it runs pretty good ( amazing what people throw away...), only i get a lot of noise in the speakers when I plug my bass guitar in the microphone port. the onboard sound card is ( from aplay -l)

card 1: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have rerouted cables inside, moved the hard disk far from everything else, still i hear a constant loud hum and high pitched whining.
So I have installed an external sound card, 
card 0: ES1938Solo1 [ESS ES1938 (Solo-1)], device 0: es-1938-1946 [ESS Solo-1]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

the system recognises it and in volume control i can see that sound is playing through it, but i hear no sound coming out the speakers. when i plug in my bass, i can see the signal indicator go up when i play a note, but i cannot hear it from the speakers. also Jack cannot connect to it, so i cannot use Rakarrack to test it.
I have tried everything i have been able to find on the net as a solution but to no avail.
I am only left with the option to ask one of you helpful geniuses to try and figure out a way to make this work.

thanks a lot

---

### Post by CrocoDuck on 2016-10-07
Try to see if the output channel of of the device is un-muted through alsamixer. In a command prompt:

```
alsamixer
```

Also, give us both

```

aplay -l
arecord -l

```

so we can see whether your device can do full duplex.

As long as ALSA recognizes the device you should be able to run jack. Make sure jack is properly configured. [This]("http://libremusicproduction.com/articles/demystifying-jack-%E2%80%93-beginners-guide-getting-started-jack") will help.

By the way, noise can be caused on your mic input by the fact you are plugging a bass to it. Bass (and guitars) are high impedance sources and don't couple well with microphone inputs. This yields to frequency response alteration and might cause noise. Consider to use a DI-BOX or a preamplifier of some kind. The best thing would be to use line inputs through DI or a pre amplifier.

---

### Post by boombox2 on 2016-10-08
boombox@boombox:~$ aplay -l **** List of PLAYBACK Hardware Devices **** card 0: ES1938Solo1 [ESS ES1938 (Solo-1)], device 0: es-1938-1946 [ESS Solo-1]   Subdevices: 2/2   Subdevice #0: subdevice #0   Subdevice #1: subdevice #1 card 1: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]   Subdevices: 0/1   Subdevice #0: subdevice #0  boombox@boombox:~$ arecord -l **** List of CAPTURE Hardware Devices **** card 0: ES1938Solo1 [ESS ES1938 (Solo-1)], device 0: es-1938-1946 [ESS Solo-1]   Subdevices: 0/1   Subdevice #0: subdevice #0 card 1: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]   Subdevices: 0/1   Subdevice #0: subdevice #0   [ATTACH=CONFIG]271537[/ATTACH]  So now Jack runs with the ESS card as input and Intel as output (is there some way i can check that?), but still no sound. in volume control i can see the meter go up when i play a note, but guitarix's tuner does not respond to the input, and that is the strange thing. I can see the card works and picks up the signal, but somehow it doesn't go through.  [ATTACH=CONFIG]271538[/ATTACH]  I have unmuted all capture channels in alsamixer, when i turn on the ones with dotted lines, the mic input automatically turns mute in volume control. However I can still see the volume meter responding to input. by the way to make the card "work" I input   sudo modprobe snd_es1938  in terminal otherwise i get no response from it. any Ideas why this card might behave like it does?  regarding the Intel card mic noise, i know that plugging the bass straight into the mic port is not the best for audio quality, however when i use my laptop in the same way, i get a pretty decent sound, only a little hum due to grounding. I have read somewhere it might be due to a driver problem, however i have not been able to find a solution that works. tanks for sharing that link, it's really a great site with lots of info, I'm having a lot of fun with it.

---

### Post by CrocoDuck on 2016-10-08
Please, try to use code blocks: it is very hard to read the output of your commands.

Both your Solo and Intel can do full duplex. Jack works best when using a soundcard only, so try to configure jack to use the Solo only (or the HDA only) and see how it goes.

> **boombox2 said:**
>    sudo modprobe snd_es1938  in terminal  otherwise i get no response from it. any Ideas why this card might  behave like it does? 

That is the kernel module needed to operate the device. [Try to make it load at boot]("https://help.ubuntu.com/community/Loadable_Modules"). It appears that you card is fully supported by ALSA, but you might require few adjustments. Here the [ALSA Matrix page]("http://www.alsa-project.org/main/index.php/Matrix:Module-es1938"). I don't think you need to do anything under "Quick Installation", as everything is already installed on your system. Perhaps, most of the adjustments described in the page are already in place in your system. You might try to create a software volume control as described in the bottom of the page. Maybe that's the reason why you keep on being muted. Just create a file called .asoundrc in your home directory (it is a hidden file) with this content:

```

       pcm.softvol {
          type softvol
          slave {
             pcm "dmix"
          }
          control {
             name "Master"
             card 0
          }
       }
       
       pcm.!default {
         type plug
         slave.pcm "softvol"
       }
```

And reboot.

---

