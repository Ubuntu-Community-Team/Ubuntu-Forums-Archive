---
title: "Help with Roland GR-55"
date: 2011-05-06
forum: Ubuntu Studio
---

### Post by jflesher on 2011-05-06
I just got a Roland GR-55 Guitar Synthesizer and I need some help setting it up. 

Basically it uses a USB connection and provides a MIDI interface via my Fender Guitar.

I have checked the web and can not find any information for setting it up on a Linux Machine.

I decided to install Ubuntu Studio 10.04 x64, so I can have an RT kernel; didn't like Unity, nor the Classic without effects in 11.04 and I'm not sure about low latency kernel vs the realtime. 

I not sure if I should see this as a device after plugging it in, but I don't.

---

### Post by jejeman on 2011-05-07
You shold have youre device listed when you do 
```
lsusb
```

---

### Post by sgx on 2011-05-07
> **jflesher said:**
> I just got a Roland GR-55 Guitar Synthesizer and I need some help setting it up. 

Basically it uses a USB connection and provides a MIDI interface via my Fender Guitar.

I have checked the web and can not find any information for setting it up on a Linux Machine.

I decided to install Ubuntu Studio 10.04 x64, so I can have an RT kernel; didn't like Unity, nor the Classic without effects in 11.04 and I'm not sure about low latency kernel vs the realtime. 

I not sure if I should see this as a device after plugging it in, but I don't.
Hi, could you explain what you would like to achieve using this device
in a linux setup? Read the docs, and web, looking for the phrase
'class compliant' in the usb sections. If it is not class compliant,
there is a good chance the midi output by usb will not work, so you would need 5 pin midi i/o connectors on a soundcard connected to those
on the gr-55. 
The line outputs can always be used to send sound to rakarrack, guitarix, calf plugins etc for further processing.
Once the midi data is streaming, zynaddsubfx reportedly has been used
as a fast responding sound module for an earlier roland GR, and yoshimi, its modernized cousin, may even be better.

Phasex synth has a clever use of your line connection, you can choose line-in as a source for its sound path.

Cheers

---

### Post by jflesher on 2011-05-07
> **jejeman said:**
> You shold have youre device listed when you do: lsusb


After a new install of Ubuntu Studio 10.04 and getting the realtime kernel to work; I had some issues with quick scan [http://wiki.linuxmusicians.com/doku.php?id=system_configuration#quickscan](http://wiki.linuxmusicians.com/doku.php?id=system_configuration#quickscan) which I got most of them fixed.

Now I see lsusb:
Bus 001 Device 008: ID 0582:0127 Roland Corp. 

Much better; now how do I get Jack connect to see it; I tried routing the system (capture 1 & 2) input to the output system (playback_1); but get no sound.

Thanks.

---

### Post by Pablo_F on 2011-05-07
> now how do I get Jack connect to see it; I tried routing the system (capture 1 & 2) input to the output system (playback_1); but get no sound.

In the setup window, make sure you tell jack to use your Roland. Now, it is probably using the onboard audio card. If you wish, show the terminal outputs of the following informative commands, and we will see:

cat /proc/asound/cards

arecord -l && aplay -l

Cheers, Pablo

---

### Post by jflesher on 2011-05-08
> **Pablo_F said:**
> 
cat /proc/asound/cards
arecord -l && aplay -l


I'm using an ASUS M4A78 Motherboard with 955 X4; 16 GB RAM; I have a Logitech 910 USB webcam connected and Nvidia 460 video card. 

GR-55 is connected with USB, I don't have a MIDI Connector on this computer.
I'll try this on other computers and see what happens.

In Windoze Vista, which I had to install as a dual boot just to test this with; I can get it to work; not that it works great; but it works; I just hate Windoze; 7 even more than Vista; which there is very little difference between them; besides the name; marketing is everything, rename it and tell people its different and works better; then sell it to them.

***
$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf7ff4000 irq 16
 1 [U0x46d0x821    ]: USB-Audio - USB Device 0x46d:0x821
                      USB Device 0x46d:0x821 at usb-0000:00:12.2-1.1, high speed

****
$ arecord -l && aplay -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: U0x46d0x821 [USB Device 0x46d:0x821], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: SB [HDA ATI SB], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by Pablo_F on 2011-05-08
Hi, 

So the roland only works as a capture device. 

In Jack Control, Setup window, left column:

interface: default
mode: duplex
input device: hw:1,0 (this is, GR-55's capture device)
output device: hw:0,0 (the onboard card's playback device)

This way, the GR-55's input ports will correspond to "system: captures" in the Connection window of Jack Control and the outputs of your normal audio card will be the "system: playbacks".

The simplest setup; connect system: captures to system: playbacks and you should be playing live. 

Cheers, Pablo

---

### Post by jejeman on 2011-05-08
> I have a Logitech 910 USB webcam connected
Does this web cam has mic?
If it does maybe that is what is seen for recording.
As far I understood that Roland is synth with separate audio conections, and over usb, it only sends midi information no audio? And you want to use it as midi controler playing notes on guitar. If that is true than you should use folowing command to determen if it shows as midi device:
```
amidi -l
```

---

### Post by jflesher on 2011-05-08
> **jejeman said:**
> 
Does this web cam has mic?
If it does maybe that is what is seen for recording.
As far I understood that Roland is synth with separate audio conections, and over usb, it only sends midi information no audio? And you want to use it as midi controler playing notes on guitar. If that is true than you should use folowing command to determen if it shows as midi device:
amidi -l


I must admit I do not know what type of information is coming across the USB connector; but in Windows I can connect Audacity as a device and record the guitar; in Linux Audacity does not show the GR-55 as a device.

Under Sound Preferences I do not see the GR-55 Device under input, but I do see the webcam, or other USB mics. So other than lsusb showing the Roland Device, I have no other indication the system recognizes it as an input device.

I did test this on another machine; same results. 

Also in Jackd I have tried to connect captured to play; I must be missing something else.

Nothing
# amidi -l
Dir Device    Name


*************************
Update:
The specs state:
USB COMPUTER connector (supports Hi-Speed USB, USB MIDI and USB Audio)
[http://www.rolandus.com/products/productdetails.php?ProductId=1148](http://www.rolandus.com/products/productdetails.php?ProductId=1148)

---

### Post by sgx on 2011-05-08
It's a simple line-out --> line-in connection, so usb is largely irrelevant for using linux software to modify or record the gr-55 signal. Choose alsa or OSS
in audacity preferences, for audacity to use your motherboard line-in
If jackd is already running when you start audacity, then you must choose that in audacity preferences, not alsa or OSS, the choice may be automatic in some distros. In the qjackctl gui, audacity will be labelled portaudio, and to get it in the gui, you must first press the audacity record button. Then pause it while you make the connections.

On some gear, Usb midi shuts down when din connectors are in use. 

Maybe get an interface with guitar i/o, mic preamp input, and 5pin midi, and you might get lucky, but the line-out should send a quality
signal to your motherboard line-in, for recording and more fx.

The gr-55 guitar-out probably sends the separated
VG-99 signal, and an optional clean preamp tone.

Timemachine is great dor simple high quality recordings using jackd,
and ardour3 beta is quite stable, youtube videos are out there, but its typical, create project, create track, arm track, press record
and play, and start the music.
Cheers

---

### Post by jflesher on 2011-05-09
I'll see if I can wrap my mind around those instructions.

Is there anyone out there that owns a Roland GR-55 Guitar Synthesizer? 
If so did you get it to work in Linux?

Connection from USB to computer is the same in Windoze and it works fine there, besides the fact its Windoze, which I don't like; Vista on top of that, since there are no drivers for Windows Server 2003 or XP x64 (same thing, different name); so I'd think it would work the same; but now its starting to look like I need a special driver.

---

### Post by jejeman on 2011-05-09
As far as I can see, you can not utilize usb connection for midi and for audio. Obviosly is not class compilant, as they say. So you need specific driver which probably does not exist for linux.
But that is not problem to use it in traditional ways of audio and midi inputs/outputs thru soundcard, as said in above post.

I would recommend to use only alsa when working with audacity. On my computer it crashes jack (ubuntu studio 11.04).

---

### Post by sgx on 2011-05-09
> **jflesher said:**
> I'll see if I can wrap my mind around those instructions.

Is there anyone out there that owns a Roland GR-55 Guitar Synthesizer? 
If so did you get it to work in Linux?

Connection from USB to computer is the same in Windoze and it works fine there, besides the fact its Windoze, which I don't like; Vista on top of that, since there are no drivers for Windows Server 2003 or XP x64 (same thing, different name); so I'd think it would work the same; but now its starting to look like I need a special driver.
Try this, record a simple pattern in windows via gr-55 usb, then,
record the exact same pattern using the line-out on the gr-55 to the
line-in on the windows sound device.
Import both .wav files into audacity, and compare them visually and sonically, and make sure the recording preferences are the same in each instance.
Cheers

---

