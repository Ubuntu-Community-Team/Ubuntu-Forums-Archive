---
title: "Newie to Ubuntu Studio"
date: 2014-02-28
forum: Ubuntu Studio
---

### Post by francisco-marzoa on 2014-02-28
Hi there!

I am new to Ubuntu Studio and would need some advice. This is my gear:

- MIDI Controller M-Audio Oxygen 61
- Electric Guitar Ibanez RG 270 '98
- Zoom G5 multieffects
- Dell XPS13 with Ubuntu Studio 13.10 

Now, I would like to produce some music. So far I have experimented with Ardour 3, Yoshimi, QSynth and Hydrogen, but I have found several issues. For example, Ardour 3 seems quite unstable at least when using MIDI tracks, so I tried with Rosegarden and QTractor but in the first case I didn't find the way to connect Rosegarden to Yoshimi so it makes sound when reproducing a track -no MIDI out from RG or something like that on jackd-, and with QTracktor I have not found a way to even save a session (the save button in the save session dialog is always greyed out).

I think I would probably come here before, so to avoid losing more time just trying things without having clear what I am doing, I would prefer to ask for some advice from more experienced Ubuntu Studio users:

[B]What I want to do now is to record some MIDI tracks for drums, piano and things like that using my M-Audio controller, and some other audio tracks mainly from my Ibanez guitar thru Zoom G5, since it provides a convenient USB audio interface.
[/B]
So, what could my best choice be?

Thanks a lot in advance,

---

### Post by jejeman on 2014-02-28
There is no best choice.
Pick a tool and learn how to use it.

My choice is MusE2 for audio and MIDI sequencing.
You need to know that there is ALSA and JACK MIDI, Yoshimi is JACK MIDI only Rosegaden probably ALSA MIDI only so you need to join them with a2jMIDI, and so on...

---

### Post by francisco-marzoa on 2014-02-28
Thanks jejeman.

I didn't know about a22jMIDI. Too many things to learn in so little time...

Do you use some sound generator like Yoshimi or so?

Bests!

---

### Post by jejeman on 2014-02-28
Yes, I use Yoshimi or ZynAddSubFx very often. Almost every time I need synth sound.
Here you can listen what my firend and I made last year only with FLOSS
[http://isidorigi.bandcamp.com/album/v](http://isidorigi.bandcamp.com/album/v)
You can hear Yoshimi in songs 2,4,6,7,8,9.

---

### Post by CrocoDuck on 2014-03-01
Hi francisco. I'm a guitar based musician too and I often record in my house with my guitars and linux box, using my midi controllers too. For the drums I'm used to use Hydrogen. It's very easy to use and you can both export the drums to audiofile or sync it with jack transport. Tons of drums sounds are avaible. With synths I use two approachs: I play them directly with the midi keyboard and I record the audio output with Ardour when I want to do some more "classical" stuff (like in the "CrocoSoul" track you find in my soundcloud page linked below) or I drive them with an instrument inside Renoise ([http://www.renoise.com/](http://www.renoise.com/)) and then I record everything into Ardour using the transport. I did this with the most "electric" tracks, like "Vision of Dystopia". As for Ardour 3.0.0, I didn't tried extensively the midi feature yet, but seemed to me pretty buggy at first glance. If I'm not wrong, a lot of improvements have been made at the actual release. So strange you cannot save with Qtractor. Have you tried File > Save As ?

---

### Post by su:bhatta on 2014-03-05
jejeman ! Lovely music you guys are making, thanks for sharing the link.

I got some time & I have listened to most of the songs in that album. Rock on.

CrocoDuck, your soundcloud is in queue, I find some time and am gonna listen to your stuff :)

---

### Post by jejeman on 2014-03-05
Thanks bhattabhishek, glad you like it.

---

