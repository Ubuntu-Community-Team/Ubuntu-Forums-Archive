---
title: "Recording Wine Output With Audacity"
date: 2011-05-29
forum: Ubuntu Studio
---

### Post by Precipitous on 2011-05-29
I am using VST Host in Wine to run some Windows VST's. I need to be able to record the output using Audacity, but can not figure out a way to get Audacity to see the audio output from Wine. Normally I have Audacity configured to work with Jack, and would love to be able to get the Wine output to be seen by Jack as well, but I can switch Audacity to ALSA if necessary...  Does anybody have any ideas?

---

### Post by Pablo_F on 2011-05-29
Hi, 

Thanks to the vestige headers, there are linux native jack-aware hosts for Windows VST effects and instruments. I suggest festige. It is in the KXstudio team PPA. 

If you keep on using a Windows host through wine, then you need wineasio which you can grab form the same PPA. wineasio is jack-aware too.

Cheers, Pablo

> Thanks to the vestige headers, there are linux native jack-aware hosts for Windows VST effects and instruments
For the record, this is not true. There were linux native jack-aware VST hosts for Linux before the vestige headers. However, thanks to them, these hosts are now free in the GPL meaning. Before the vestige headers, you had to compile the hosts yourself against the propietary and free as in beer VST-SDK headers. Binary distribution was not allowed by the VST SDK licence. For many of us, beginners at that time, no packages meant no joy, so vestige was very welcome.

---

### Post by Precipitous on 2011-05-29
> **Pablo_F said:**
> Hi, 

Thanks to the vestige headers, there are linux native jack-aware hosts for Windows VST effects and instruments. I suggest festige. It is in the KXstudio team PPA. 

If you keep on using a Windows host through wine, then you need wineasio which you can grab form the same PPA. wineasio is jack-aware too.

Cheers, Pablo
I have tried Festige and it locks up my computer as soon as I launch a vst. In fact, I have tried all of the native Linux hosts and have had horrible results. Wine is my last attempt. I already have WineASIO installed and have configured Wine to use Jack, but for some reason Jack is not seeing it...

---

### Post by Pablo_F on 2011-05-29
The way it used to work for me: You don't select the jack driver in wine configuration, only alsa (go figure).

Then, in the Windows host you select the wineasio driver. 

This worked for me in my tests in Reaper and FLstudio.

Don't forget to register wineasio.dll!

Cheers, Pablo

---

### Post by Precipitous on 2011-05-30
> **Pablo_F said:**
> The way it used to work for me: You don't select the jack driver in wine configuration, only alsa (go figure).

Then, in the Windows host you select the wineasio driver. 

This worked for me in my tests in Reaper and FLstudio.

Don't forget to register wineasio.dll!

Cheers, Pablo
Pablo - Thank you for the tips. Unfortunately, they open up another can of worms...

If I set Wine to use ALSA, and VstHost to use WineASIO, I am able to see VstHost in Jack, and am able to trigger VST's using my MIDI controller, yet I get no sound. I know that the VST is outputting it because I can see the meters in VstHost running properly. Unfortunately, I can not hear a thing. If I do an audio test in Wine, I get the error message: Audio Failed. The messages from Jack indicate the following:

10:20:22.952 JACK is starting...
10:20:22.953 /usr/bin/jackd -p128 -t5000 -dalsa -dhw:0 -r44100 -p128 -n3 -S
10:20:22.956 JACK was started with PID=22161.
no message buffer overruns
no message buffer overruns
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2011 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK server starting in realtime mode with priority 10
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|128|3|44100|0|0|nomon|swmeter|-|16bit
control device hw:0
configuring for 44100Hz, period = 128 frames (2.9 ms), buffer = 3 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 3 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 3 periods for playback
Clock source : system clock via clock_gettime
10:20:23.156 JACK connection change.
10:20:23.157 Server configuration saved to "/home/gslater/.jackdrc".
10:20:23.158 Statistics reset.
10:20:23.165 Client activated.
10:20:23.174 JACK connection graph change.
Clock source : system clock via clock_gettime
10:20:38.960 ALSA connection graph change.
10:20:39.279 JACK connection graph change.
10:20:39.402 JACK connection graph change.
10:20:39.590 JACK connection change.
10:20:39.751 JACK connection graph change.
[B]JackEngine::XRun: client = vsthost was not run: state = 2
JackAudioDriver::ProcessGraphAsync: Process error
10:20:40.660 XRUN callback (1).[/B]
10:20:40.693 JACK connection graph change.

If I set Wine to use Jack, I am able to get audio from VstHost, and am able to configure it with Jack to be available in Audacity, but I can not get VstHost to see any MIDI devices. No controller, no way to play notes, except to use a mouse on VstHost's virtual keyboard...

I am absolutely stumped!

---

### Post by sgx on 2011-05-30
[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)

there are jackd connections guides at this link.

It sounds like the audio output device for vsthost is not
selected, or is not routed to your soundcard, or is going
to the wrong one if you have 2. Or a mixer is off.

We must select input-output hardware devices in the chosen vst host
preferences, (as well as the asio driver) and again in qjackctl, jp1, or patchage, so we connect the virtual cables properly. Some things autoconnect, others not.

With alsa chosen in wine, qjackctl presents 3 tabs in the connection panel, the right tab is for alsa midi ports, as found on your midi
keyboard, and soundcard.

The left tab is for routing audio signals between a soundcard,
and various softwares, capture on the left, playback on the right.

Some folks have different input and output devices, others have both on one device, so in qjackctl, open the Setup page, and at

Input Device  >
Output Device >

click the > widgets to view and choose your desired sound devices.
Midi keyboard on the right half connects to soundcard midi port on the left.
Some gear requires a proprietary asio driver, and won't work, and
some plugins don't work.

Only use 3 in jackd periods/buffer settings for a usb device,
even numbers for the rest.

Cheers

---

### Post by Precipitous on 2011-05-31
> **sgx said:**
> 

It sounds like the audio output device for vsthost is not
selected, or is not routed to your soundcard, or is going
to the wrong one if you have 2. Or a mixer is off.

We must select input-output hardware devices in the chosen vst host
preferences, (as well as the asio driver) and again in qjackctl, jp1, or patchage, so we connect the virtual cables properly. Some things autoconnect, others not.

Cheers
Sgx- Thanks for the information...

I use qjackctl for configuration, routing, etc. and already have the correct software/hardware/MIDI connections made. Do you have any other ideas as to what is going on?..  I find it interesting that if Wine is set to ALSA, MIDI works fine but audio doesn't, and yet if I have it set to Jack audio works fine but MIDI doesn't...

---

### Post by Pablo_F on 2011-05-31
Have you tried increasing the frames per period value? 
And maybe the synchronous mode (by appending -S to the jackd command in the server path field)?
Or perhaps, increasing the timeout value?
What audio card do you have? Are you absolutely sure jack is using it? If you have more than one, sometimes the numbers get mixed up. 

What plugin are you trying to run? I would like to test. 

Is this your VST Host?
[http://www.hermannseib.com/english/vsthost.htm](http://www.hermannseib.com/english/vsthost.htm)

Note that you always need ALSA in wine configuration for MIDI, as there is not jack MIDI support in wine, afaik. You can select both ALSA and jack at the same time in winecfg. However, I don't think you need jack in winecfg, just wineasio output in VST Host (Devices -> Wave -> Output port). Make sure to select the right (=the same as in jack) sample rate and period value.

Sorry for repeating but, did you do a:

**regsvr32 wineasio.dll**

in a terminal?
 
Another test:

When you are running VST Host in "no audio mode", please, run the following commands and show the terminal outputs:

ps aux |grep jackd
lsof | grep pcm

---

### Post by Precipitous on 2011-05-31
> **Pablo_F said:**
> Have you tried increasing the frames per period value? 
And maybe the synchronous mode (by appending -S to the jackd command in the server path field)?
Or perhaps, increasing the timeout value?

What plugin are you trying to run? I would like to test. 

Is this your VST Host?
[http://www.hermannseib.com/english/vsthost.htm](http://www.hermannseib.com/english/vsthost.htm)

Pablo - Thank you for your continued help!

I have not tried increasing the frames per period or timeout values yet, but I will do so this afternoon when I get home from work. I have not tried synchronous mode either...

The link you have to VstHost is correct. I think you will find it to be a really wonderful utility, should you end up figuring out a way around the problems I have been experiencing. Unfortunately, I get the same result no matter which VST I try to run in it.

---

### Post by Pablo_F on 2011-05-31
I have just tried with the battery demo and it works for me. 

OK, please report back. You are welcome!

---

### Post by sgx on 2011-05-31
I just tested Vsthost, normally use Reaper.

I placed its folder in the wine Program Files folder.

I had to select wineasio in the menu Devices --> Wav --> Output Port

and select the midi input and output devices in the adjoining Midi menu.

I loaded Synth1, and Amplitube Fender, and it worked fine on both,
good to go for guitars and keys.

I checked jp1, and qjackctl, and vsthost was auto-connected in both,
same as Reaper, in all cases.

I wonder if pulseaudio is snatching the sound? Reboot and issue command:
killall pulseaudio (it will have no output, if successful)

then start the vst setup.

Cheers
also I noticed the asio wave output needed to be selected each time
after stopping and starting Vsthost. Cantabile12lite also behaves this way,
Reaper finds wineasio on its own.

---

### Post by Precipitous on 2011-06-01
> **Pablo_F said:**
> Have you tried increasing the frames per period value? 
And maybe the synchronous mode (by appending -S to the jackd command in the server path field)?
Or perhaps, increasing the timeout value?
What audio card do you have? Are you absolutely sure jack is using it? If you have more than one, sometimes the numbers get mixed up. 

What plugin are you trying to run? I would like to test. 

Is this your VST Host?
[http://www.hermannseib.com/english/vsthost.htm](http://www.hermannseib.com/english/vsthost.htm)

Note that you always need ALSA in wine configuration for MIDI, as there is not jack MIDI support in wine, afaik. You can select both ALSA and jack at the same time in winecfg. However, I don't think you need jack in winecfg, just wineasio output in VST Host (Devices -> Wave -> Output port). Make sure to select the right (=the same as in jack) sample rate and period value.

Sorry for repeating but, did you do a:

**regsvr32 wineasio.dll**

in a terminal?
 
Another test:

When you are running VST Host in "no audio mode", please, run the following commands and show the terminal outputs:

ps aux |grep jackd
lsof | grep pcm

I tried each one of your suggestions and nothing has changed...

The output of ps aux |grep jackd is:
gslater  22818  1.3  0.7  40364 28404 ?        SLsl 00:10   0:01 /usr/bin/jackd -p128 -t1000 -dalsa -dhw:0 -r44100 -p256 -n2 -S
gslater  24458  0.0  0.0   4008   764 pts/0    S+   00:12   0:00 grep --color=auto jackd

The output of lsof | grep pcm is:
jackd     22818    gslater  mem       CHR      116,5                4063 /dev/snd/pcmC0D0p
jackd     22818    gslater  mem       CHR      116,6                4066 /dev/snd/pcmC0D0c
jackd     22818    gslater    6u      CHR      116,5      0t0       4063 /dev/snd/pcmC0D0p
jackd     22818    gslater    7u      CHR      116,6      0t0       4066 /dev/snd/pcmC0D0c

---

### Post by Pablo_F on 2011-06-01
Do you see wineasio audio ports at all?

In these conditions, what is the output of 

jack_lsp -c

?

---

### Post by Precipitous on 2011-06-01
> **Pablo_F said:**
> Do you see wineasio audio ports at all?

In these conditions, what is the output of 

jack_lsp -c

?
Pablo:

Are you asking if I see wineasio audio ports in the Jack Connections tab? If so, the answer is yes (and I have them connected properly to be able to monitor them). If you are asking if I see them in VstHost, the answer is again yes (I have wineasio selected as the wave device, and when I play I see the meters in VstHost indicate that audio is present, but I can not hear anything).

Unfortunately, I am not at my home computer right now, so the output of jack_lsp -c will have to wait for a later post...

p.s. Thank you for taking the time to try and help with this one. I really appreciate it!

---

### Post by Precipitous on 2011-06-01
> **Pablo_F said:**
> Do you see wineasio audio ports at all?

In these conditions, what is the output of 

jack_lsp -c

?
Pablo - 

The output of jack_lsp -c is:

Clock source : system clock via clock_gettime
system:capture_1
system:capture_2
system:playback_1
   vsthost:out_1
system:playback_2
   vsthost:out_2
system:playback_3
system:playback_4
system:playback_5
system:playback_6
system:playback_7
system:playback_8
vsthost:in_1
vsthost:in_2
vsthost:in_3
vsthost:in_4
vsthost:in_5
vsthost:in_6
vsthost:in_7
vsthost:in_8
vsthost:in_9
vsthost:in_10
vsthost:in_11
vsthost:in_12
vsthost:in_13
vsthost:in_14
vsthost:in_15
vsthost:in_16
vsthost:out_1
   system:playback_1
vsthost:out_2
   system:playback_2
vsthost:out_3
vsthost:out_4
vsthost:out_5
vsthost:out_6
vsthost:out_7
vsthost:out_8
vsthost:out_9
vsthost:out_10
vsthost:out_11
vsthost:out_12
vsthost:out_13
vsthost:out_14
vsthost:out_15
vsthost:out_16

---

### Post by sgx on 2011-06-02
> **Precipitous said:**
> I am using VST Host in Wine to run some Windows VST's. I need to be able to record the output using Audacity, but can not figure out a way to get Audacity to see the audio output from Wine. Normally I have Audacity configured to work with Jack, and would love to be able to get the Wine output to be seen by Jack as well, but I can switch Audacity to ALSA if necessary...  Does anybody have any ideas?
There is a quirk with audacity and jackd, with Jack Connection Kit selected in audacity preferences -->Devices -->Host,
press record in audacity,
then press pause, then go to qjackctl, and look for portaudio, that will be your audacity connection.
Press pause again, to resume recording when the connections are made.
I just tested using Vsthost, and it worked fine.
(edit: this may have been fixed in the latest audacity betas)

Hope this helps.

alsamixergui shows all the possible sound outputs, should sound
be going to an odd location.
Cheers

---

### Post by Precipitous on 2011-06-02
> **sgx said:**
> There is a quirk with audacity and jackd, with Jack Connection Kit selected in audacity preferences -->Devices -->Host,
press record in audacity,
then press pause, then go to qjackctl, and look for portaudio, that will be your audacity connection.
Press pause again, to resume recording when the connections are made.
I just tested using Vsthost, and it worked fine.
(edit: this may have been fixed in the latest audacity betas)

Hope this helps.

alsamixergui shows all the possible sound outputs, should sound
be going to an odd location.
Cheers
I appreciate your taking the time to help...  I work with both jack and audacity a lot, though (I recorded my last three albums using Audacity), so I am used to the various routing quirks... Unfortunately in this instance the same problems occur whether I am using Audacity, QTractor, etc... 

Since you are not experiencing the same issues, I am curious as to what distro and build you are running, what sound card, Wine version, etc. I am running Maverick, Wine 1.3 and Intel HDA audio...  Perhaps there is a version/conflict problem happening?

---

### Post by sgx on 2011-06-02
Hi, I'm using pclinuxos E17 lite, with debian unstable audio apps converted to rpm, and wine 1.2.3-2  wineasio 7.3 audacity 1.3.13

bodhi linux (E17 distro) with debian unstable audio apps, wine 1.3.
wineasio 9.1 (Falk PPA)

and Puppy Studio, based on lucid repos.

maudio 24/96 pci soundcard, the hda_intel chip is blacklisted

try recording with this app, installed with

dpkg -i timemachine_0.3.3-1_i386.deb

[http://packages.debian.org/unstable/sound/timemachine](http://packages.debian.org/unstable/sound/timemachine)

Cheers

---

### Post by Pablo_F on 2011-06-02
Strangely, the vsthost client here is called "ASIO_vsthost". 

It could be what you say. I am running Dream Studio Lucid with some packages from KXstudio and Autostatic PPA's. 

wine --version: wine-1.3.8
wineasio 0.7.5-1

VstHost works with the wineasio driver. Tested VST's are: Studio Devil (audio to audio) and Battery (MIDI to audio). 

I prefer festige though ("winetricks allfonts" comes handy).

Cheers, Pablo

---

### Post by Precipitous on 2011-06-03
I was finally able to get everything working perfectly by using [SaviHost]("http://www.hermannseib.com/english/savihost.htm") to host VST's instead of [VstHost]("http://www.hermannseib.com/english/vsthost.htm"). It is a stripped down version of [VstHost]("http://www.hermannseib.com/english/vsthost.htm"), created by the same person, that runs just one VST at a time.

Thank you Pablo_F and sgx for all of your suggestions and assistance. You are both greatly appreciated!

---

### Post by sgx on 2011-06-04
Good news! Just in time for the weekend :)

---

