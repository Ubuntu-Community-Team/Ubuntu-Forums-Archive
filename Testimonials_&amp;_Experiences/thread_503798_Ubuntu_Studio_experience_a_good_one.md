---
title: "Ubuntu Studio experience a good one"
date: 2007-07-18
forum: Testimonials &amp; Experiences
---

### Post by theorganloft on 2007-07-18
:guitar:I set up a recording system for my church and needed a way to edit, stream, and produce audio CDs.  We bought a CDRW recorder and found that they work well but are unreliable.  
The first audio workstation was based on Windoze XP using Audacity as the audio editing package.  It worked well but we needed other audio and midi applications and the church winced at the price of Pro Tools, Cakewalk, and the other proprietary software packages. 
I told them about some of the Open Source Solutions such as Ardour, Rosegarden, Hydrogen, etc.. and they agreed to take a look.
I built an AMD2/1GB/250Gb Sata super quiet computer with a Soundblaster Live and loaded Mepis 6.x on it with Audacity, K3b, Rosegarden, and other music software. We tested and they loved it. It was also extremely reliable in live stressful recording sessions where the CDRW recorder would fail and this system would keep chugging along.
I upgraded the entrie system to Ubuntu Studio and the system is even faster and has more features than ever. They love it!:guitar:

---

### Post by loserboy on 2007-07-18
that's awesome man

---

### Post by MetalMusicAddict on 2007-07-18
You're welcome. We think Ubuntu Studio-Gutsy will even better. We're currently working to make things a little tighter.

---

### Post by theorganloft on 2007-07-18
Appreciate the response.  I look forward to the new version but wanted to point out some installation tips to others:

[LIST]
If you are doing live recording, turn off local speaker settings, sounds, beeps etc
You must use the synaptic package manager to load K3B (CD\DVD creator) and Libmp3lame0(audacity mp3 encoder)
Jack is not started by default and you will have to configure it to start during boot.  You need Jack for the Synths and Hydrogen. 
[/LIST]

These are important for live audio. 
The sound quality is excellent even for the SB Live card.  I was astonished at the clarity so imagine if I used an even higher quality interface. :guitar:

I look forward to the new version. My next machine will be dedicated to Video Recording, Editing, and Streaminig and I will attempt to use Ubuntu Studio.

---

### Post by wolfen69 on 2007-07-18
glad to hear it's working out for you and the church.

---

### Post by theorganloft on 2007-07-19
> **wolfen69 said:**
> glad to hear it's working out for you and the church.

I ran into an issue on a new system. 

I installed US (Ubuntu Studio) on the machine and decided to change the sound card to a Echo Mia Midi.  

All hell broke loose.  It does not even see the card after boot. I tried to load the ALSA drivers to no avail.  

What am I doing wrong?:confused::confused::confused:

Should the system recognize a supported ALSA card automatically

---

