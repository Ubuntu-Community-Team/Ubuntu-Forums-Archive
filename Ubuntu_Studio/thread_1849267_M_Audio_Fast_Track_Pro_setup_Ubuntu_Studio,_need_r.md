---
title: "M Audio Fast Track Pro setup Ubuntu Studio, need realy good help"
date: 2011-09-24
forum: Ubuntu Studio
---

### Post by noisemaker? on 2011-09-24
hello,

i have a siemens lifebook a530. i want to use the m audio fast track pro usb Interface with ubuntu studio... i have allready messed up more then 3 ubuntu installations because the usb interface is not working with ubuntu... i used to have an old firewire interface wich runs with ffado no problem, but this m audio fast track pro doesent work at all... i dont see either the Inputs or the Outputs anywhere, it is just frustrating and i don't know anymore where to bang my head on.. the table, the wall or maybe it is easier to just fall of the chair...

anyways, i have now clean installed ubuntu studio again and have not changed any settings so far... please someone help me to get this interface running with 4 Outs and 2 Ins... I have already searched the web and found about thousand of hits, but nothing really solved the problems but made it worse

thanks...

---

### Post by jejeman on 2011-09-24
Lets, start ;)
give us output
```
lsusb
```
```
aplay -l
```
```
arecord -l
```

---

### Post by noisemaker? on 2011-09-24
hello, thanks... here is my output:

**lsusb **

mark@noisemaker1:~$ lsusb
Bus 002 Device 004: ID 0763:2012 Midiman M-Audio Fast Track Pro
Bus 002 Device 003: ID 1532:0003 Razer USA, Ltd Krait Mouse
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 1690:0741 Askey Computer Corp. [hex] 
Bus 001 Device 003: ID 05c8:030e Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mark@noisemaker1:~$ ^C
mark@noisemaker1:~$ 

**aplay -l**

mark@noisemaker1:~$ aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC269 Analog [ALC269 Analog]
  Sub-Geräte: 0/1
  Sub-Gerät #0: subdevice #0
Karte 0: Intel [HDA Intel], Gerät 3: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: Pro [FastTrack Pro], Gerät 0: USB Audio [USB Audio]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: Pro [FastTrack Pro], Gerät 1: USB Audio [USB Audio #1]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
mark@noisemaker1:~$ 

**arecord -l**

mark@noisemaker1:~$ arecord -l
**** Liste der Hardware-Geräte (CAPTURE) ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC269 Analog [ALC269 Analog]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: Pro [FastTrack Pro], Gerät 1: USB Audio [USB Audio #1]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
mark@noisemaker1:~$

---

### Post by jejeman on 2011-09-24
The card is recognized. As playback and as recording device.
Do you want to use it with JACK or with pulseaudio?

---

### Post by noisemaker? on 2011-09-24
i think i got it running now, but i dont know how and i dont know why... and i swear the fkn channels did not show up before no matter what i have done...

this forum post helped me a bit.. it says that the m audio fast track runs as two devices and you musst choose hw:1,1 in qjackctl... so i did that and it seemed to work, but without the output channel... after i have messed up the hole **** some more jack wouldnt start anymore at all.. after i have shut down the pc and switch on / of the interface, i see all input and output channels.. but not as hw:1,1 but as hw:0 wich is funny because i swear it never did show up all channels with hw:0

so if you have any problems you might need to mess around a little with the input and output settings of qjackctl... the hw:1,1 option wont show up in the standard drop down field, it is hidden by the button right next to it with the arrow on it.. then it shows you all available hw i/o

[http://ardour.org/node/744](http://ardour.org/node/744)

i will now try some recording... thanks for all help... so lucky it finaly seems to work.. until next reboot? :D

---

### Post by jejeman on 2011-09-24
Yes, thats exactly it. You need to choose device in qjackctl.

---

### Post by noisemaker? on 2011-09-24
well, it is not working. i was just happy to early... it looked like it, but it is not working, if i choose hw:1 jack will start but only give me the 2 Outs... When i choose device hw:1,1 like the posting of the other forum said, jack wont start

maybe i should buy a firewire interface and use ffado

edit:

i have now tried any possible configurations in jack and it gets more and more frustrating, i got jack starting either with 2 inputs or 2 outputs but not both in and outs and all 4 outs i don't see either. it seems like this m audio fast track pro is working not well with linux at all

---

### Post by jejeman on 2011-09-24
I see there are 2 output devices: 1,0 1,1
I don't know how is the device configured, maybe the outputs are separated 2+2. If thats so, you can have only 2 channels at one time.
Did you tried with 1,0 to have 4 outputs?

---

### Post by sgx on 2011-09-24
Try the envy24control mixer, for maudio devices, it may be part
of the alsa-tools-gui package in synaptic, or maybe separate.
It lists all the i/o on my audiophile 24/96 pci card OK

The Chw: Phw: ID changes depending on what is plugged in when you boot, the config file qjackctl writes is

/home/username/.jackdrc mine at the moment is

/usr/bin/jackd -P89 -t1000 -dalsa -r44100 -p256 -n3 -D -Chw:1 -Phw:0,0

you can issue it's content as a command, modified as desired.
Choose your sound devices for input and out device. The jackd manpage
has all the options described, so over the next few weeks, you can
see which ones help your setup. Note the -n3, usb devices should use
3, in the qjackctl Periods/buffer setting

the -p256 is qjackctl Frames/period setting, the lower, the better, until unwanted noises say it's too low.

C-apture h-ard w-are  is Chw:x.x
P-layback h-ard w-are  is Phw:x,x

These can be different, my example has a usb guitar input,
and maudio soundcard output.

if the command
ps ux

reveals some pulse.xxx is running, use the command

killall pulseaudio

Make sure a web browser or skype etc has not started before jackd,
as they may grab the audio.

Cheers

---

### Post by nandinga on 2011-09-26
Hi, just landed on the thread and didn't read it all to be honest, but I was on the same situation a couple of months ago with the FTP.

The interface si USB1, and it follows the standards for that kind of interface and therefor works, but not at full potential (ie, not at  24/96).

The only way to get that working now is to patch the kernel. You'll also like to have a realtime kernel (well fully preemptible)with IRQ threading and do some tweaks so you could follow this guide:

[http://joegiampaoli.blogspot.com/2011/06/m-audio-fast-track-pro-for-debian-linux.html](http://joegiampaoli.blogspot.com/2011/06/m-audio-fast-track-pro-for-debian-linux.html)

The problem with that approach is that it is not best done with ubuntu based distros, nor with the latest kernels (see the versions of the patches).

The good news is that the patch for the FTP has been finally submitted to the Alsa project (same as ffdao but for usb and pci interfaces) and will be out with kernel 3.1. And regarding realtime stuff, that is all includen in vanilla kernel since 2.9 ...yay!!

So, you can just wait for those to arrive to your favorite distro by themselves.

Cheers!!

---

