---
title: "No JACK USB audio output"
date: 2011-02-06
forum: Ubuntu Studio
---

### Post by onewayness on 2011-02-06
Hi all.

Having trouble with JACK audio output through a USB interface.

Recording guitars and such through an ART USB Dual Pre, which I just received yesterday.  Plugged it in, and it worked right out of the box.  Configuration in JACK was very straightforward, and had no trouble getting tones from Rakarrack/JackRack/Guitarix etc., and getting processed signal through my headphone out of the preamp.

Then of course I put it away and brought it back out again, and now it doesn't work...  :-/

I can still hear the dry signal from the preamp, but no return signal from JACK.  It's not just the guitar signal, synths and other JACK-connected things aren't sounding either.  I know the input is working, I'm still able to successfully record it in Ardour, even.  I just can't hear it.

Both input and output devices are set to hw:1 / USB Audio CODEC, which is what was working yesterday.  Tried alternate USB cables and everything I could think of, and no dice.

Any help would be appreciated...

---

### Post by Pablo_F on 2011-02-06
Hi, 

Check your hardware connections. I think it is better if you connect the monitor outputs left and right to an external amplifier, instead of the headphone output, that you normally use for hardware monitoring. Anyway, what is the setting of the MIX knob?

On the software side, in Jack Control, I think it is better if you leave the input and output devices as (default) and choose your soundcard in the interface field, so that jack will hopefully default to the right input/output device (duplex mode).

I suggest you use aqualung to test the playback (software center). Make sure that the aqualung (or whatever) output ports are connected to the system: playback input ports (which correspond to the output ports of the card that jack is using for playback) in the connect window of Jack Control (audio tab), or in patchage (blue connections).

We can help better if you give the terminal output of the command:

arecord -l && aplay -l

and show the messages of Jack Control.

Cheers, Pablo

---

### Post by onewayness on 2011-02-06
Hi Pablo.

Using the monitor outs to an external amp & speakers is not going to work most of the time, as I'll be using this for portable recording with my laptop.

The MIX knob - when it's panned to 'Preamp' I hear the dry signal from the preamp, and when panned to 'Computer' I hear nothing.

I tried as you suggested and changed the input and output channels to (default) and the interface tab to hw:1, and same result.

Aqualung appears to play, but no audio.

Terminal output & JACK messages below, thanks for the help.

Adam


arecord -l && aplay -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


22:58:04.065 JACK is starting...
22:58:04.066 /usr/bin/jackd -dalsa -dhw:1 -r44100 -p256 -n2
22:58:04.072 JACK was started with PID=2681.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
control device hw:1
control device hw:1
audio_reservation_init
Acquire audio card Audio1
creating alsa driver ... hw:1|hw:1|256|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:1
Using ALSA driver USB-Audio running on card 1 - Burr-Brown from TI               USB Audio CODEC  at usb-0000:00:1d.0-1, full s
configuring for 44100Hz, period = 256 frames (5.8 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback
22:58:06.214 JACK connection change.
22:58:06.217 Server configuration saved to "/home/adam/.jackdrc".
22:58:06.219 Statistics reset.
22:58:06.229 Client activated.

---

### Post by Pablo_F on 2011-02-07
Hi, 

I don't know what happens but you can try a lower level test: speaker-test 

[http://alsa.opensrc.org/Speaker-test](http://alsa.opensrc.org/Speaker-test)

I think, someting like:

speaker-test -Dfront:default -c2 -twav

should give sound when the knob is panned to computer. If not, post the output of *aplay -L* please.

EDIT: stop the jack server before running speaker-test

Cheers, Pablo

---

### Post by sgx on 2011-02-07
> **onewayness said:**
> Hi all.

Having trouble with JACK audio output through a USB interface.

Recording guitars and such through an ART USB Dual Pre, which I just received yesterday.  Plugged it in, and it worked right out of the box.  Configuration in JACK was very straightforward, and had no trouble getting tones from Rakarrack/JackRack/Guitarix etc., and getting processed signal through my headphone out of the preamp.

Then of course I put it away and brought it back out again, and now it doesn't work...  :-/

I can still hear the dry signal from the preamp, but no return signal from JACK.  It's not just the guitar signal, synths and other JACK-connected things aren't sounding either.  I know the input is working, I'm still able to successfully record it in Ardour, even.  I just can't hear it.

Both input and output devices are set to hw:1 / USB Audio CODEC, which is what was working yesterday.  Tried alternate USB cables and everything I could think of, and no dice.

Any help would be appreciated...
If the ART preamp is the HW:1, then it can't be both the input and output, your souncard/chip needs to be the output device. Qjackctl
setup page,

Input device  >
Output device >

click the  >  and see your options.

If you have a second usb device, like an m-audio usb soundcard,
then it may have changed its hw: number on a fresh boot. I have a
bootable usb drive, usb guitar amp, and usb modem, all in use at
irregular times, so some horesplay is needed to sort the hw: in
qjackctl. 

Cheers

---

### Post by Pablo_F on 2011-02-07
> If the ART preamp is the HW:1, then it can't be both the input and output

Why not? :) hw:1 or hw:default is the USB card and the device hw:1,0 has both capture and playback ports. 

**** List of CAPTURE Hardware Devices ****
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
**** List of PLAYBACK Hardware Devices ****
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]

This card is not just a preamp, it is a class compliant usb soundcard 16bit/44,1kHz with input and output connections. The OP does not need to choose the input and output devices separately as they want to use the USB card in duplex mode (for capture and playback). 

OTOH, jack gives no errors. To narrow down the sources of the problem, I suggested the speaker-test. 

Cheers, Pablo

---

### Post by onewayness on 2011-02-07
@Pablo:  The speaker test failed, see below...


adam@adam-HP-Mini:~$ speaker-test -Dfront:default -c2 -twavPlayback open error: -16,Device or resource busy

speaker-test 1.0.23

speaker-test: invalid option -- '1'
Unknown option '?'
adam@adam-HP-Mini:~$ speaker-test -Dfront:default -c2 -twav

speaker-test 1.0.23

Playback device is front:default
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy
Playback open error: -16,Device or resource busy



adam@adam-HP-Mini:~$ aplay -L 
default
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Hardware device with all software conversions
front:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    Front speakers
surround40:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    Direct sample mixing device
dsnoop:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    Direct sample snooping device
hw:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    Direct hardware device without any conversions
plughw:CARD=default,DEV=0
    USB Audio CODEC , USB Audio
    Hardware device with all software conversions
adam@adam-HP-Mini:~$

---

### Post by Pablo_F on 2011-02-07
Hi, 

Did you stop the jack server before running speaker-test? You also might need to kill pulseaudio (the default audio server in ubuntu) but in this case, you also need to avoid autospawn. In a terminal:

echo "autospawn=no" > ~/.pulse/client.conf
pulseaudio -k
killall jackd
speaker-test -Dfront:default -c2 -twav

Cheers, Pablo

---

### Post by onewayness on 2011-02-07
Hi Pablo.  

No, I hadn't killed JACK first, I thought you had meant for me to run the script with it running.  Tried it per your instructions, and it executed, but I heard nothing.  Should this have sounded through my internal speaker, or through the preamp?

I tried resetting JACK to hw:0 for the outputs, and I hear playback normally through my laptop's internal sound card.  Switched it back to hw:1, and again nothing through the preamp...

Thanks,
Adam

adam@adam-HP-Mini:~$ echo "autospawn=no" > ~/.pulse/client.conf
adam@adam-HP-Mini:~$ pulseaudio -k
adam@adam-HP-Mini:~$ killall jackd
jackd: no process found
adam@adam-HP-Mini:~$ speaker-test -Dfront:default -c2 -twav

speaker-test 1.0.23

Playback device is front:default
Stream parameters are 48000Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 96 to 262144
Period size range from 48 to 131072
Using max buffer size 262144
Periods = 4
was set period_size = 65536
was set buffer_size = 262144
 0 - Front Left
 1 - Front Right
Time per period = 5.543955
 0 - Front Left
 1 - Front Right
Time per period = 5.547827

etc etc etc...

---

### Post by Pablo_F on 2011-02-07
Hi, 

> 
No, I hadn't killed JACK first, I thought you had meant for me to run the script with it running.
No, I wanted you to leave jack or any other audio server out of the equation. Now it seems that jack is not to blame, that the problem is in a lower level (in the hardware or the alsa driver).

Try with 44100 frame rate (adding the -r44100 option):

speaker-test -Dfront:default -r44100 -c2 -twav

This command tests your interface called "hw:default" which is the USB audio interface. Sorry for this again, buy I suppose you have the MIX knob set to computer.

I suggest you try with the monitor outs to an external amplifier, with speaker-test and jack-aqualung. 

> Should this have sounded through my internal speaker, or through the preamp?
Through the USB card, of course. To test the laptop speakers, just to hear what you should be hearing through the ART USB Dual Pre, modify the command:

speaker-test -Dfront:Intel -c2 -twav

Cheers, Pablo

---

### Post by onewayness on 2011-02-09
> **Pablo_F said:**
> Now it seems that jack is not to blame, that the problem is in a lower level (in the hardware or the alsa driver).

Try with 44100 frame rate (adding the -r44100 option):

speaker-test -Dfront:default -r44100 -c2 -twav



This gave me an error, as the playback frame rate didn't match the frame rate of the test .wav, see below.

It would make sense that I may not have been able to hear the 48khz audio through the ART, as its max frame rate is 44.1khz.  Any thoughts how to fix this?

JACK is definitely set at 44.1 btw...

adam@adam-HP-Mini:~$ speaker-test -Dfront:default -r44100 -c2 -twav

speaker-test 1.0.23

Playback device is front:default
Stream parameters are 44100Hz, S16_LE, 2 channels
WAV file(s)
Rate set to 44100Hz (requested 44100Hz)
Buffer size range from 90 to 262144
Period size range from 45 to 131072
Using max buffer size 262144
Periods = 4
was set period_size = 65536
was set buffer_size = 262144
Sample rate doesn't match (48000) for /usr/share/sounds/alsa/Front_Left.wav

> **Pablo_F said:**
> Sorry for this again, buy I suppose you have the MIX knob set to computer.

I suggest you try with the monitor outs to an external amplifier, with speaker-test and jack-aqualung. 


Yes, MIX is set 100% to computer.

Will try via external amp later tonight and report back...

> **Pablo_F said:**
> To test the laptop speakers, just to hear what you should be hearing through the ART USB Dual Pre, modify the command:

speaker-test -Dfront:Intel -c2 -twav


This worked perfectly.

Thanks again for all the help so far.

adh

---

### Post by Pablo_F on 2011-02-09
> This gave me an error, as the playback frame rate didn't match the frame rate of the test .wav
My bad, sorry. 

> It would make sense that I may not have been able to hear the 48khz audio through the ART, as its max frame rate is 44.1khz. Any thoughts how to fix this?

Probably, but as you point out, you are telling jackd to use 44.100 Hz. Anyway, this should give pink noise at 44100 Hz on your USB card:

speaker-test -Dfront:default -r44100 -c2

Again, use "Intel" instead of "default" to test the laptop speakers.

Cheers, Pablo

---

### Post by sgx on 2011-02-10
> **Pablo_F said:**
> Why not? :) hw:1 or hw:default is the USB card and the device hw:1,0 has both capture and playback ports. 

**** List of CAPTURE Hardware Devices ****
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]
**** List of PLAYBACK Hardware Devices ****
card 1: default [USB Audio CODEC ], device 0: USB Audio [USB Audio]

This card is not just a preamp, it is a class compliant usb soundcard 16bit/44,1kHz with input and output connections. The OP does not need to choose the input and output devices separately as they want to use the USB card in duplex mode (for capture and playback). 

OTOH, jack gives no errors. To narrow down the sources of the problem, I suggested the speaker-test. 

Cheers, Pablo
Hi, I've seen nothing in several ads to indicate this device is a soundcard.
As an input device, I would connect its pre-amped signal to the soundcard or motherboard soundchip, which would be selected as the output device. Then connect the output of that motherboard soundchip, or soundcard, to timemachine, ardour, audacity etc for recording.

typical ad info:

"The ART USB Dual Pre is ideal for laptop-based audio production. It's powered by an internal 9-volt battery, your computer's USB bus, or an optional 12-volt DC adapter. The rugged aluminum chassis with rubber sides handles road abuse.

The ART USB Dual Pre has two low-noise input channels with XLR balanced and 1/4" TRS inputs, each with up to 48dB of clean gain and clip LED indicators. With it's low noise 48-volt phantom power supply you can power up to two mics as well as the preamp when running off any of the power sources. The 1/4" outputs are buffered and low impedance balanced for use as either preamplifier outputs or feeds for powered monitors. A rear 1/8" TRS mini headphone jack with level and monitor controls provides latency-free monitoring of inputs during recording or the USB bus during playback. Fully compliant with the USB 1.1 specification, this compact device uses USB adaptive mode for playback and USB asynchronous mode for recording."

Monitoring a signal, vs. rendering input signals which would be sent to line/headphone outputs, or down the usb bus, are not equal tasks.
Cheers.
:)

---

### Post by onewayness on 2011-02-12
> **Pablo_F said:**
> Anyway, this should give pink noise at 44100 Hz on your USB card:

speaker-test -Dfront:default -r44100 -c2

Again, use "Intel" instead of "default" to test the laptop speakers.


Tested it through the laptop, and got pink noise.  Tested it though 'default', and nothing from the USB.  Tried both the speaker test and Aqualung through external amp also, and nothing.

Seems this is looking increasingly like a hardware issue?

adh

---

### Post by onewayness on 2011-02-12
> **sgx said:**
> Hi, I've seen nothing in several ads to indicate this device is a soundcard.
As an input device, I would connect its pre-amped signal to the soundcard or motherboard soundchip, which would be selected as the output device. Then connect the output of that motherboard soundchip, or soundcard, to timemachine, ardour, audacity etc for recording.



So, you're suggesting I need to send the audio monitor outs of the preamp to the audio in of my existing soundcard?  Sort of defeats the whole purpose of this being a USB interface, no?

adh

---

### Post by Pablo_F on 2011-02-12
> Seems this is looking increasingly like a hardware issue?

Yes. See if you can test it in another laptop with Windows but try with the main outputs anyway.

Cheers, Pablo

---

### Post by onewayness on 2011-02-12
> **Pablo_F said:**
> Yes. See if you can test it in another laptop with Windows but try with the main outputs anyway.


I'm tempted to just return it and try another of the same unit.  Kinda baffling that it essentially worked out of the box and then suddenly quit on the first day of use...

---

### Post by Matthew0025@hotmail.com on 2011-05-19
Hi I also have a problem trying to connect my TRS wired speakers to my computers and i don't know how to create a new thread so can sum1 help me?? btw it is a dell speaker

---

