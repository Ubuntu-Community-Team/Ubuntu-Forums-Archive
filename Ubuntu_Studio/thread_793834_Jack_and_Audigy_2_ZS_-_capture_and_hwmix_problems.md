---
title: "Jack and Audigy 2 ZS - capture and hwmix problems"
date: 2008-05-14
forum: Ubuntu Studio
---

### Post by Ryukage on 2008-05-14
I've recently acquired an Audigy 2 ZS (the basic version, w/o the front box or remote) to replace my onboard sound, and I'm having some trouble getting it to work properly with JACK. I went to a lot of trouble to get this card specifically because I'd read in numerous sources that it had the best ALSA support of any, so I'm rather irritated that I can't get it to work correctly.

The card shows up in qjackctl as five possible devices (ignoring the general hw:0 device):

hw:0,0 - ADC Capture/Standard PCM Playback (duplex)
hw:0,1 - Mic Capture (capture)
hw:0,2 - Multichannel Capture/PT Playback (duplex)
hw:0,3 - Multichannel Playback (playback)
hw:0,4 - p16v (duplex)

Now, hw:0,0 works fine, but it's of little use: there's only two output channels and it doesn't capture the Mic or Line In data, it just loops playback back into the capture ports.

Selecting hw:0,1 as a capture device doesn't work at all, the sample rates go all screwy and jackd kills itself in the face of continuous xruns. I don't consider this a big problem because...

hw:0,2 seems to work fine as a capture device, gets the Mic channel at least, probably Line In as well though I haven't tested that. However, I haven't checked that all sixteen capture channels work--I suspect they don't because...

While hw:0,3 works for playback, only the first two of the sixteen channels produce any sound.

All of the above use the emu10k2 DSP chip, which only supports 16-bit/48kHz sampling. The last one, hw:0,4, represents the p16v DSP chip, which handles 24-bit/96kHz sampling. Output to the p16v works as well as the Multichannel Playback, which is to say only the first two of the sixteen channels produces sound, but if I select the p16v for capture, jackd kills itself:

> jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
loading driver ..
Enhanced3DNow! detected
SSE2 detected
apparent rate = 96000
creating alsa driver ... hw:0,4|hw:0,4|1024|2|96000|0|0|hwmon|hwmeter|-|32bit
control device hw:0
configuring for 96000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 32bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit little-endian
ALSA: use 2 periods for playback
03:48:30.086 Server configuration saved to "/home/msd/.jackdrc".
03:48:30.091 Statistics reset.
03:48:30.108 Client activated.
03:48:30.112 Audio connection change.
03:48:30.134 Audio connection graph change.
03:48:30.138 XRUN callback (1).
JACK tmpdir identified as [/dev/shm]
Enhanced3DNow! detected
SSE2 detected
03:48:32.125 XRUN callback (96 skipped).
jackd watchdog: timeout - killing jackd
zombified - calling shutdown handler

Makes no difference if I select a different playback device or sample rate.

Can anyone help me
1) get hardware mixing working with either hw:0,3 or hw:0,4
and
2) get 24/96k Mic and Line In capture working.

I'm using Kubuntu 7.10 x86-64 with the realtime kernel.

---

### Post by Ryukage on 2008-05-17
Found part of the answer to problem 1 myself, though I still don't have it working. The ld10k1 and qlo10k1 packages contain software to reconfigure the internal routing of the emu10k[1,2] chipset, which is needed to set up hardware mixing--the default config set up by ALSA is suitable for normal desktop usage, but is not ideal for production. Unfortunately, the software as it appears in the gutsy repo doesn't seem to work. I can't get qlo10k1 to actually make a connection, and lo10k1 (the CLI version) gives me a wierd error message that makes no sense. If they aren't fixed by Hardy+1, maybe I'll do some hacking myself.

Still don't understand why I can't use the p16v pathway for capture, though, and that's the more important issue.

---

### Post by supergenius23 on 2008-06-04
I have the same card and the same problem... Did you ever get the sound to work? I am only getting sound on p16v

---

### Post by Ryukage on 2008-10-14
> **supergenius23 said:**
> I have the same card and the same problem... Did you ever get the sound to work? I am only getting sound on p16v

Sorry for taking so long to reply...

No, I've not made any progress getting things to work. In fact, what I said earlier about playback working with the p16v turned out be incorrect--Jack doesn't crash immediately, but does as soon as I try to actually send data to the card. Same symptoms as with capture, Jack reports a huge number of xruns then zombifies.

So for me, the p16v doesn't work, period. The emu10k1 part of the card works fine, except for not being able to reconfigure the where the FX channels go.

I'm still using 7.10, as I don't yet have Linux-compatible internet access, which makes upgrades rather painfull. That should change in a couple of months, so maybe newer versions of ALSA will work.

---

### Post by aldur999 on 2008-10-16
Umh, have you tried checking/uncecking Audigy Analog/Digital Outpout Jack in alsamixer?

PS, sorry for my bad english..

---

### Post by Ryukage on 2008-11-20
> **aldur999 said:**
> Umh, have you tried checking/uncecking Audigy Analog/Digital Outpout Jack in alsamixer?

Yes. The problem occurs whether that's on or off.

---

### Post by flatko on 2008-11-22
I have Audigy SE - almost the same issue: In duplex mode, it gives a lot of xruns, in capture or playback it doesn't. Qlo10k1 gives me "cannot connect to socket" when i try to add a soundcard.

I'm using feisty at this time, but i dont believe that this is the point.
Since WinXP is useless for me, until I get a fix for this, I'll keep using my onboard sound for any recording...

---

### Post by LuthiAir on 2008-12-03
I had the same problem.
This was my solution.

In the Jack configuration, choose "Multichannel Capture/PT Playback (duplex)" for both Input and Output.

Then change the number of channels for both input and output to 16.

In the volume control (not jack), you also want to check the "analog/digital output" box.

That eliminated all the xruns I was getting and let me do realtime recording into Ardour along side existing tracks that were being played back live.

This solution worked in Ubuntu Studio as well as 64Studio.

Good Luck

---

### Post by Ryukage on 2008-12-05
> **LuthiAir said:**
> In the Jack configuration, choose "Multichannel Capture/PT Playback (duplex)" for both Input and Output.

Then change the number of channels for both input and output to 16.

In the volume control (not jack), you also want to check the "analog/digital output" box.

That eliminated all the xruns I was getting and let me do realtime recording into Ardour along side existing tracks that were being played back live.

I can't tell if this is meant as a solution for flatko specifically or the thread in general, but if it is the latter...

Yes, that eliminates the xruns, but you only get 16-bit samples, because that device corresponds to the Emu10k2 chip, which is only a 16-bit chip. You need to go through the p16v chip for 24-bit operation, and that's what doesn't work.

I don't know about the SE's architecture, but the ZS is essentially two separate sound cards wired to the same physical connections. One is a 16-bit Emu10k2 chipset that's basically equivalent to the onboard sound on most mobos these days, except it has MIDI synth. The second is the 24-bit p16v chipset, which is what makes the card worth having if you've already got Emu10k2 onboard sound.

---

### Post by willcoq on 2009-02-14
I'm a similar problem in that I'm trying to configure my Yamaha DGX-500 midi keyboard to work with my Audigy 2 ZS in Ubuntu. Should I just get the Midi>USB adapter? Or would I still have the same issues?

---

### Post by shaddyz on 2010-09-13
I've done it! I've got the p16v to work for playback and recording!

HW Information: Creative Labs Sound Blaster Audigy 2 ZS Platinum Pro

There is a lot of information that could prove to be useful to getting this to work for you, but I'm going to include what I think will be most helpful, and if you need to know anything else, let me know!

[SIZE=3]UBUNTU[/SIZE]
10.04 LTS "Lucid Lynx"

[SIZE=3]LINUX[/SIZE]
I'm using the **realtime** kernel 2.6.31-11-rt

[SIZE=3] ALSA[/SIZE]
Default configuration

[SIZE=3] PULSE AUDIO[/SIZE]

file: **/etc/pulse/daemon.conf**

    ```

default-sample-format = s24le
default-sample-rate = 48000

```file: **/etc/pulse/default.pa**
```

    load-module module-alsa-sink   device=hw:0,4 rate=48000 sink_name=p16v_output
    load-module module-alsa-source device=hw:0,4 rate=48000 source_name=p16v_input

    set-default-sink   p16v_output
    set-default-source p16v_input

```I also commented out automatic device detection because I only want to use the p16v

[SIZE=3] ALSA MIXER[/SIZE]

The p16v output volume is controlled by the "HD Analog" levels. A value of "81" represents 0.0 dB of gain. If you set it higher, the audio will be distorted.

[SIZE=3] JACK[/SIZE]

First thing, don't use qjackctl! Start jackd manually.

```
jackd --realtime -d alsa --rate 48000 --capture hw:0,4 --playback hw:0,4
```[SIZE=3]ARDOUR[/SIZE]

I let Ardour start jackd for itself otherwise it will die from inactivity.

Ardour Audio Setup:

* DEVICE TAB*

Driver: ALSA
Interface: p16v
Sample rate: 48000Hz
Buffer size: 1024
Number of buffers: 2
Audio Mode: Playback/Recording on 2 Devices

* OPTIONS TAB*

Realtime checked
Realtime Priority: 90

** DONE!**

Hope this helps! Let me know if you have any questions.

---

### Post by shaddyz on 2010-09-18
I decided to re-enable the **emu10k** because it seems the **headphone output jack** on the breakout box is only powered by that chip. I may have also been experiencing other problems from it unknowingly.

In addition, I have been having some issues with **playback using Rhythmbox**. At first, it would repeatedly disconnect from Pulse. I assumed Pulse was crashing and restarting. After doing some research, I found a solution which was to reinstall the package for gstreamer to use pulse ***gstreamer0.10-pulseaudio*** (10.04 lucid lynx). But after resolving that issue, yet another one arose; every once in a while Rhythmbox will complain of an error playing a file, **pa_stream_writable_size() failed: Connection terminated**, and it will skip to the next song and play it normally. I am also noticing odd behavior skipping tracks in a manner that suggests it's due to the root cause. I am in the process of understanding their behavior to see if I can match it with a previously solved problem.

The following are the lines I added to /etc/pulse/**default.pa** in order to re-enable the emu10k *without* using autodetect.

```

load-module module-alsa-sink   device=hw:0,0 rate=41100 sink_name=emu10k_output
load-module module-alsa-source device=hw:0,0 rate=41100 source_name=emu10k_input

```

---

### Post by EpicFai1 on 2010-10-01
Well, I'm not even as close as you guys all are. I am a beginning user and have just recently picked up a camera and mic so I can try out some multi track recording. But after putting Ubuntu studio control on my computer. I have been unable to connect to JACK at all. It is telling me:
p, li { white-space: pre-wrap; } JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
 Your system has an audio group, but you are not a member of it.
 Please add yourself to the audio group by executing (as root):
   usermod -a -G audio (null)
After applying these changes, please re-login in order for them to take effect.You don't appear to have a sane system configuration. It is very likely that you encounter xruns. Please apply all the above mentioned changes and start jack again!
[COLOR=#999999]13:06:56.968 JACK was started with PID=9752.[/COLOR] [COLOR=#999999]13:06:56.977 JACK was stopped with exit status=255.[/COLOR]
[COLOR=#999999]13:06:56.978 Post-shutdown script...[/COLOR] [COLOR=#990099]13:06:56.978 killall jackd[/COLOR]
jackd: no process found [COLOR=#999999]13:06:57.390 Post-shutdown script terminated with exit status=256.[/COLOR]
[COLOR=#FF0000]13:06:59.093 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]
--What can I change to allow myself to use this system so I can operate my multi track software? - assist please

---

### Post by Pablo_F on 2010-10-01
Hi, 

Open a terminal an type:

sudo usermod -a -G audio your_user_name

And reboot.

That should do it.

Also, if you don't mind giving the output of:

aplay -l 

so we can know something more about your audio interface so we can prevent further little probs because alsa sometimes get confused with audio cards ID numbers.   Sorry for the broken English.

Cheers! Pablo

---

### Post by EpicFai1 on 2010-10-01
> **Pablo_F said:**
> Hi, 

Open a terminal an type:

sudo usermod -a -G audio your_user_name

And reboot.

That should do it.

Also, if you don't mind giving the output of:

aplay -l 

so we can know something more about your audio interface so we can prevent further little probs because alsa sometimes get confused with audio cards ID numbers.   Sorry for the broken English.

Cheers! Pablo
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
--is the info that was posted for me. I have it working now, through a different post(but thank you). Only issue I have now is getting my audio recording devices to register my mic, as well as getting the video programs, since I only have the audio programs right now through ubuntu studio control.
~assist please

---

### Post by Pablo_F on 2010-10-01
Please, can you open a new thread?

title could be:

Intel ICH5 through JACK, no mic capture, no sound on video players.

Or something of the sort.

And put the output of:

aplay -l
cat /proc/asound/cards
cat /proc/asound/modules
cat /proc/asound/card0/codec#0 |grep -i codec

and a short description of the problem.

I will help there. 

Cheers! Pablo

---

