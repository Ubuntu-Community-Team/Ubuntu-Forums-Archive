---
title: "M audio Oxygen8 + Synth"
date: 2011-02-13
forum: Ubuntu Studio
---

### Post by Sylos on 2011-02-13
Hello and thanks for looking.

I am now the proud owner of an M audio Oxygen8 USB midi keyboard. It appears to be in working order. It appears in the ALSA section of Jack Connections and I have connected it to Qsynth and it triggers the little green LED when I press the keys. However, Im not getting any sound.

I assume this is because the soundfonts in Qsynth need some sound coming from an input device (eg Virtual Keyboard) to then impose the parameters of the font on it. So now we get to the point of my post....

What suggestions do people have for how to achieve this? I really want the sounds to be pumped through Qsynth as this is where I am getting the sound I want from, BUT, I want to limit the number of apps required to do it as my system is old (Athlon 2ghz with 768mb RAM - awful I know).

Any insights and/or suggestions welcome.

Cheers

---

### Post by AutoStatic on 2011-02-13
Did you connect Qsynth's audio outputs to your soundcard's input ports in QjackCtl? And what soundfont are you using? And your MIDI keybaord is the input device, so no need for virtual keyboards. And there isn't any sound going into Qsynth, only MIDI messages. Those messages trigger the different notes from the bank in the soundfount you selected.
And congrats on the M-Audio Oxygen8! Is it the v2 one?

Best,

Jeremy

---

### Post by Pablo_F on 2011-02-13
> I assume this is because the soundfonts in Qsynth need some sound coming from an input device (eg Virtual Keyboard)

No, qsynth needs a MIDI input and that comes from a virtual keyboard, a midi sequencer... OR from a hardware midi keyboard. You have that part right. 

Assuming qsynth already has a soundfont loaded, press the Channels button.

You should see the green LED in one of them. This channel has to have a bank and Program, i.e. an instrument that belongs to one of the loaded soundfonts. Is it there?

In the simplest case, you choose the instrument in a given channel in qsynth. The MIDI channel is set in the MIDI keyboard. This way you can prepare up to 16 instruments from the soundfont.

EDIT: Hi Auto, I haven't seen your post! :) 

Of course, make sure that qsynth's audio outputs are connected to system: playbacks in the audio tab of qjackctl's connections.

Cheers, Pablo

---

### Post by Sylos on 2011-02-15
> **AutoStatic said:**
> Did you connect Qsynth's audio outputs to your soundcard's input ports in QjackCtl? And what soundfont are you using? And your MIDI keybaord is the input device, so no need for virtual keyboards. And there isn't any sound going into Qsynth, only MIDI messages. Those messages trigger the different notes from the bank in the soundfount you selected.
And congrats on the M-Audio Oxygen8! Is it the v2 one?

Best,

Jeremy

Cheers for the post Jeremy. 

This is the V2 Oxygen8 and it seems pretty sweet.

I have now got it playing some sounds from my Soundfont (im putting the first abortive attempted down to, er, 'pilot error' perhaps? Anyhow, I now have a slightly different problem.

When connected to Zynaddsubfx the keyboard works perfectly BUT when connected to Qsynth using my own soundfont it behaves weirdly. There are anomolies in the velocity of the key stroke and the sound produced - ie some normal keystrokes illicite a sound as if a very soft stroke had been applied. Also, some keystrokes dont seem to register at all - no sound!

I wonder if this is down to a problem with the software or a problem with my soundfont. I created all my soundfonts in the most basic way using SWAMI. I imported some WAV samples and just added them as left and right - no fancy layering or other frills. Could my lamefonts by the source of the irratic behaviour?

Also, on a more general note, can you point me in the direction of some guidance on how to set up all the knobs and dials on the Oxygen8 to trigger settings on Zynnadd and Qsynth?


Many thanks to you both.

EDIT: Also, I noticed the Oxygen8 does not show up in the MIDI tab of Qjackctl - it is in the ALSA tab. Is this normal?

---

### Post by madeinfamous on 2011-02-15
hi Sylos,

*Also, on a more general note, can you point me in the direction of some guidance on how to set up all the knobs and dials on the Oxygen8 to trigger settings on Zynnadd and Qsynth?*

if this could help, the first link is the Oxy8v2 manual in english,
[URL="https://docs.google.com/viewer?a=v&pid=explorer&chrome=true&srcid=0BwwZfJr1t_YGNTFjZTVhZjgtZjY2My00ZDUxLTk2MmUtNjdkYTlmZTllOWZh&hl=fr&authkey=CNzfhv0C"]Oxygen_UG_EN.PDF
[/URL]

this one I made it as a reminder for my setting, just sharing it, it take patience to understand, just like linux! :)
[setting-up oxygen and software]("https://docs.google.com/leaf?id=0BwwZfJr1t_YGZWFhY2ZkODMtMWJkZi00YTRjLTk1YjUtZWFkMDdmYTdiMzRi&hl=fr&authkey=CPLW26kD")

anyway, have fun with your new toy!

a nice week to all :)

---

### Post by AutoStatic on 2011-02-15
> **Sylos said:**
> This is the V2 Oxygen8 and it seems pretty sweet.It is, but be careful with it (mine is broken :( )

> **Sylos said:**
> When connected to Zynaddsubfx the keyboard works perfectly BUT when connected to Qsynth using my own soundfont it behaves weirdly. There are anomolies in the velocity of the key stroke and the sound produced - ie some normal keystrokes illicite a sound as if a very soft stroke had been applied. Also, some keystrokes dont seem to register at all - no sound!Did you try another soundfont? Does another soundfont have that erratic behaviour too?

> **Sylos said:**
> Also, on a more general note, can you point me in the direction of some guidance on how to set up all the knobs and dials on the Oxygen8 to trigger settings on Zynnadd and Qsynth?You have to program that on your Oxygen8 with the help of the user manual and the ZynAddSubFX MIDI bindings documentation: [http://zynaddsubfx.sourceforge.net/doc_3.html](http://zynaddsubfx.sourceforge.net/doc_3.html)

For Qsynth, no idea, I barely use it and afaik it only responds to some very basic MIDI messages (volume, pitchbend, panning).

> **Sylos said:**
> EDIT: Also, I noticed the Oxygen8 does not show up in the MIDI tab of Qjackctl - it is in the ALSA tab. Is this normal?Try running **a2jmidid -e &** in a terminal after having started up QjackCtl and Jack. This will export all current ALSA MIDI ports so they will become available in the JACK MIDI tab of QjackCtl. But for ZASFX and Qsynth this is not necessary as they both create ALSA MIDI ports (ZASFX is ALSA MIDI only, Qsynth creates ALSA MIDI ports by default).

Best,

Jeremy

---

