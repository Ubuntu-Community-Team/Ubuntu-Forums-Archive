---
title: "Midi &lt;-&gt; USB interface"
date: 2012-03-15
forum: Ubuntu Studio
---

### Post by JohnReid on 2012-03-15
Hi,

I have a Technics SX-P50 electronic piano and a Dell laptop running Ubuntu 11.10 (not Ubuntu Studio but I thought you people would be the best to ask). I want a midi connection between the piano and the laptop. I'm guessing I'll be able to play tracks on the piano and record them as midi files then overlay other tracks on top of those later on. Also it would be nice to use the piano to control a software synthesizer. I'm also guessing the best thing for me to get is a midi->USB connector. Can anyone recommend one? Is a Cakewalk UM-1G going to work? I don't want to spend too much. Is latency an issue?

On another note, what software can I use to transcribe what I play into musical notation?

Thanks in advance for any help,
John.

---

### Post by sgx on 2012-03-15
Hi, if the midi device packaging mentions driverless OSX support it should work.
Musecore is a cross-platform notation system. Rosegarden sequencer utilizes lilypond, for quality notation output.

softsynth:
calf monosynth

dssi system has qsynth GUI for fluidsynth(soundfont player),
hexter DX7 sysex player,
whysynth, a deep wavetable synth, ray_v, a new dssi synth with good sound

standalone synths: phasex, yoshimi/zynaddsubfx, hydrogen drum machine for /sample-pattern-playback

qtractor, rosegarden, muse, seq24 all offer an array of capabilities.

Windows plugins without dongles or notorious copy protection,
work well in Reaper daw, requires wine and wineasio.

Cheers

---

### Post by JohnReid on 2012-06-08
Thanks for the help. I finally ended up buying a [UM-ONE]("http://www.roland.com/products/en/UM-ONE/") which seems to do the job just great so far. I've been messing around with rosegarden and hydrogen but I think there is a lot to learn.

---

### Post by sgx on 2012-06-10
Hi, timemachine is a good recording software, when started,
it opens a simple green record button/meter gui, look in qjackctl,
and connect hydrgen, or other output to it, and press record
button when ready. It saves 24 bit files with a .w64 extension.

These can be played in vlc media player, and imported
into audacity, for editing and conversion.

To easily overdub a second part, press play and pause the file in vlc, connect vlc to timemachine in qjackctl, along with the instrument used for the overdub, and press record on timemachine, then press play on vlc, and 

:guitar:

To use yoshimi synth, and others, run the command

a2jmidid -j default

this opens a jack-midi connection in the middle Midi tab
of qjackctl.

Phasex synth opens its midi connection in the Alsa tab, and
auto-connects in the Audio tab.

Hydrogen has a midi port in the alsa tab, when connected,
you can 'fingerdrum' on the midi keyboard, to embellish it's
drum playing patterns.

when Calf-plugins are installed, look in /usr/bin
for calfjackhost, or similar, or maybe its in an audio menu,
when its gui appears, calf monosynth is great fun for leads
played over drums/synths/guitars etc

The many calf-plugins, phaser, chorus, reverb etc are among
the finest!

hexter is a gui tp play Yamaha DX7 sysex banks (google deckard sysex
to get a huge collection.) They are 32 sounds per bank, and really
come alive when used with rakarrack multi-fx app, calf, or other
plugins. Install LV2core, Invada, and MDA lv2 plugins, if not yet
in your system.
Cheers

---

### Post by BcRich on 2012-06-10
Wow, that's useful info! Thanks sgx :)

---

