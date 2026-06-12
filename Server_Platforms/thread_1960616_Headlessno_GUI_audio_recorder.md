---
title: "Headless/no GUI audio recorder"
date: 2012-04-17
forum: Server Platforms
---

### Post by MakOwner on 2012-04-17
I need to record audio through the mic/line-in jack via scripts.
I want to use the minimal install disk (using 10.04 LTS) for the base install then install just enough to get the arecord utility loaded and functioning.  

I have a Dell pe850 with an ASUS PCIe sound card- from lscpi -v:
```

02:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
	Subsystem: ASUSTeK Computer Inc. Device 8275
	Flags: bus master, medium devsel, latency 32, IRQ 16
	I/O ports at ec00 [size=256]
	Capabilities: [c0] Power Management version 2
	Kernel driver in use: AV200
	Kernel modules: snd-virtuoso


```

This works fine when I run the live cd version of 10.04 LTS desktop, and I can install to the local disk and so long as I install the full desktop it works.

I have tried the following:

minimal install + alsa 
minimal install + pulseadio
minimal install + alsa + pulseaudio

Everything I can find for troubleshooting require GUI tools.
Can anyone point me at something that will help?
I can't even get a reply over in the multimedia forum.

---

### Post by rubylaser on 2012-04-18
I've never tried doing what you are attempting, but it should be possible with just Alsa.  What does your script look like, and have you unmuted your mic input in alsamixer?  You could also try to record the audio with SOX.

---

### Post by MakOwner on 2012-04-18
> **rubylaser said:**
> I've never tried doing what you are attempting, but it should be possible with just Alsa.  What does your script look like, and have you unmuted your mic input in alsamixer?  You could also try to record the audio with SOX.

I have this working on some older equipment, so I know it's possible.
I'm using a new sound card (PCIe instead of the old PCI sound card).

This new hardware works exactly as I expect it to when I load the desktop install.

I used the alsamixer application to run the mic input up from 0 to 81(%?) on the input panel, so I'm assuming the mic is unmuted.  I'm not familiar with alsamixer - am  I missing something?

---

### Post by MakOwner on 2012-04-18
> **rubylaser said:**
> I've never tried doing what you are attempting, but it should be possible with just Alsa.  What does your script look like, and have you unmuted your mic input in alsamixer?  You could also try to record the audio with SOX.

I use arecord and lame to record off the mic and lame to convert and tag the wav to mp3. pertinent section of the cron job:

```

print "begin recording at `date` ..."
arecord -c 2 -f U8 -r 44100 -t wav -d $SECONDS $STGDIR/$SHOW/$NAME.wav
print "end recording at `date` ..."

print "begin conversion at `date` ..."
lame --silent --tt "$TT" --ta "$TA" --tl "$TL" --ty "$TY" --tn "$TN" --tg "$TG" -h -V6 --add-id3v2 $STGDIR/$SHOW/$NAME.wav $STGDIR/$SHOW/mp3/$NAME.mp3
print "end conversion at `date` ..."

```

---

### Post by MakOwner on 2012-04-19
Really?  No one does audio with command line tools?
Do I just have bad breath and now one wants to talk?

---

### Post by rubylaser on 2012-04-19
I'd love to help, but like I said, I've never done this or felt the need.  You can toggle alsa's muted state by pressing the m key, but if you're seeing a percentage in the mic column, it's not muted.  Have you tried to record something with SOX?

---

### Post by egpetrich on 2012-04-20
I use a server to capture audio from an FM tuner card. Like you, I use the "arecord" utility, as in:

```
arecord -t wav -f S16_LE -d ${LENGTH} -r ${RATE} -c ${NUM_CHAN} \
  ${HOME}/audio/radio/${NAME}.wav
```

Getting everything set up correctly can be troublesome. I definitely think you need to get comfortable with "alsamixer". Some thoughts:
First, make sure that the "card" and "chip" fields in the upper left make sense.
Second, alsamixer draws a distinction between playback and capture. You start in "playback" view, as shown on the "view" line:

```
View: F3:[Playback] F4: Capture  F5: All
```

To switch to "capture" view, press TAB. On my system, possible capture devices are:

[LIST]
[*]Line
[*]CD
[*]Mic
[*]Video
[*]Phone
[*]Aux
[*]Mix
[*]Mix Mono
[/LIST]

Only one of these can have the "CAPTURE" tag assigned. I think you would want to select "Line." Use the arrow keys to move the selector over to "Line" and press SPACE.

On my system, there's a separate bar marked "Capture". The capture devices above don't have volume indicators, only the "Capture" bar. Pressing SPACE while on the "Capture" bar turns the volume bar on and off. (When selected, I see "CAPTURE <80/80> Capture".)

Turning the capture level up too high can result in distortion. I've worked out that setting the capture level at 80/80 is sufficient for my purposes.

In summary:

[LIST=1]
[*]Start "alsamixer".
[*]Press TAB to reach the capture screen.
[*]Use the left and right arrow keys to select "Line", then press SPACE to select.
[*]Use the left and right arrow keys to select "Capture".
[*]If you don't see "CAPTURE Capture", press SPACE to turn capture on.
[*]Use the up and down arrow keys to adjust the capture level.
[*]Press ESC to exit "alsamixer".
[/LIST]

My system saves the mixer state when the system shuts down, and then restores it on boot.

---

### Post by MakOwner on 2012-04-20
> **egpetrich said:**
> I use a server to capture audio from an FM tuner card. Like you, I use the "arecord" utility, as in:

```
arecord -t wav -f S16_LE -d ${LENGTH} -r ${RATE} -c ${NUM_CHAN} \
  ${HOME}/audio/radio/${NAME}.wav
```


I'd be using a card if I could find one that worked.  I have a number of old(er) devices sitting in the closet because it tirned out whil portions of stuff worked, it was way too much hassle to get working.  I just run a male-to-male line from the ear phone jack on a cheapy FM radio to the mic jack on the server.  

[QOTE]
Getting everything set up correctly can be troublesome. I definitely think you need to get comfortable with "alsamixer". Some thoughts:
First, make sure that the "card" and "chip" fields in the upper left make sense.
Second, alsamixer draws a distinction between playback and capture. You start in "playback" view, as shown on the "view" line:

```
View: F3:[Playback] F4: Capture  F5: All
```

To switch to "capture" view, press TAB. On my system, possible capture devices are:

[LIST]
[*]Line
[*]CD
[*]Mic
[*]Video
[*]Phone
[*]Aux
[*]Mix
[*]Mix Mono
[/LIST]

Only one of these can have the "CAPTURE" tag assigned. I think you would want to select "Line." Use the arrow keys to move the selector over to "Line" and press SPACE.

On my system, there's a separate bar marked "Capture". The capture devices above don't have volume indicators, only the "Capture" bar. Pressing SPACE while on the "Capture" bar turns the volume bar on and off. (When selected, I see "CAPTURE <80/80> Capture".)

Turning the capture level up too high can result in distortion. I've worked out that setting the capture level at 80/80 is sufficient for my purposes.

In summary:

[LIST=1]
[*]Start "alsamixer".
[*]Press TAB to reach the capture screen.
[*]Use the left and right arrow keys to select "Line", then press SPACE to select.
[*]Use the left and right arrow keys to select "Capture".
[*]If you don't see "CAPTURE Capture", press SPACE to turn capture on.
[*]Use the up and down arrow keys to adjust the capture level.
[*]Press ESC to exit "alsamixer".
[/LIST]

My system saves the mixer state when the system shuts down, and then restores it on boot.[/QUOTE]



You are walking me down the right track here I think.  
I have never had the need for alsamixer, the old machine I used for this worked with no change after install.

So -- open alsamixer and the upper left hand corner displays the card name "Xonar XD".  I press f6 and I see on "default" , "0 Xonar DX"
and "enter device name..."

In the playback view, all the sliders that are visible are at 90<>90 under the green background box with 00 under the slider. That's Master Front, Master Rear, Master Center, Master Woofer, Master Side and Analog Input Monitor (It's either 100 or 0 - currently at 100).  Front Panel, Mic Boost and S/PDIF have boxes with, but no sliders.

In the Capture view  I have Line, Mic, Aux and Analog Input Monitor.

Line has no volume and can only be on or off.  Selecting the mic with the line turned on or off I can raise or lower the slider but there is nothing that indicates that it's on/off/muted and the "m" key has no effect.

Any ideas?

---

### Post by MakOwner on 2012-04-21
> **egpetrich said:**
> I use a server to capture audio from an FM tuner card. Like you, I use the "arecord" utility, as in:

Would you mind sharing what tuner card you use?
I would love to move away from the physical radio connected to a mic jack.
I would imagine a card would allow you to tune in software too?

---

### Post by MakOwner on 2012-04-21
I have been working through this guide:
[http://www.support.emtrion.de/doku.php?id=linux:linux_audio]("http://www.support.emtrion.de/doku.php?id=linux:linux_audio")

I tried setting recording to the mic and I get this output:
```


# amixer sset "Mic" cap
Simple mixer control 'Mic',0
  Capabilities: cvolume cvolume-joined cswitch cswitch-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 31
  Mono: Capture 28 [90%] [7.50dB] [on]
# amixer sset "Mic Input" on
amixer: Unable to find simple control 'Mic Input',0

# amixer sset "Output Mixer Line Bypass" on
amixer: Unable to find simple control 'Output Mixer Line Bypass',0


```


So, I'm missing something more than just alsa settings. I think. :/

---

### Post by egpetrich on 2012-04-28
I haven't used "amixer" before, so I'm working on only a few minutes worth of experience. However, I think that your sound card may use different names than "Mic Input" and "Output Mixer Line Bypass". The command:

```
amixer scontrols
```

shows a complete list of what the man page calls "simple mixer controls". The command:

```
amixer scontents
```

shows the list of controls as well as their settings. On my system, I don't see "Mic Input" or "Output Mixer Line Bypass".

I'd still recommend sticking with "alsamixer", since it wraps stuff together into a GUI that is conceptually similar to what you'd see under MS Windows or X Windows (don't know how Macs do this).

I had to open my server's case to verify that I am using a Hauppauge WinTV-Radio card of very old vintage (purchased 2004). It's a PCI card, for one thing; for another, it receives only NTSC analog signals, so it's definitely no good any longer for receiving over-the-air TV signals here in the U.S.

Hauppauge's Web page shows some new PCI-E WinTV cards with FM tuners. You have to go to "TV tuners for system builders" to find them, though. I have no idea if these newer cards have support under Linux.

For my card, the package "fmtools" provides command-line support for turning the radio receiver off and on, tuning the frequency, and setting the radio volume, all with a single command called "fm". Pretty handy. I had a refresher course in setting it up because I just today migrated the card to a different system. All appears well, but tonight's recording will put it to the test.

---

### Post by MakOwner on 2012-04-28
> **egpetrich said:**
> I haven't used "amixer" before, so I'm working on only a few minutes worth of experience. However, I think that your sound card may use different names than "Mic Input" and "Output Mixer Line Bypass". The command:

```
amixer scontrols
```

shows a complete list of what the man page calls "simple mixer controls". The command:

```
amixer scontents
```

shows the list of controls as well as their settings. On my system, I don't see "Mic Input" or "Output Mixer Line Bypass".

I'd still recommend sticking with "alsamixer", since it wraps stuff together into a GUI that is conceptually similar to what you'd see under MS Windows or X Windows (don't know how Macs do this).

I had to open my server's case to verify that I am using a Hauppauge WinTV-Radio card of very old vintage (purchased 2004). It's a PCI card, for one thing; for another, it receives only NTSC analog signals, so it's definitely no good any longer for receiving over-the-air TV signals here in the U.S.

Hauppauge's Web page shows some new PCI-E WinTV cards with FM tuners. You have to go to "TV tuners for system builders" to find them, though. I have no idea if these newer cards have support under Linux.

For my card, the package "fmtools" provides command-line support for turning the radio receiver off and on, tuning the frequency, and setting the radio volume, all with a single command called "fm". Pretty handy. I had a refresher course in setting it up because I just today migrated the card to a different system. All appears well, but tonight's recording will put it to the test.


Thank you for sharing the information.

---

