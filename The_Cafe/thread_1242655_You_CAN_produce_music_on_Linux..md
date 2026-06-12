---
title: "You CAN produce music on Linux."
date: 2009-08-17
forum: The Cafe
---

### Post by Mazza558 on 2009-08-17
Here's a video I made showing off what the free Linux synthesizer and sequencer, LMMS, can do. I can't stand people who say it's hard to make or produce music on Linux. With LMMS, it's easier than ever and certainly no harder than the lengths people sometimes have to go to get wifi or other drivers working on Ubuntu.

Either way, here's the video: [http://www.youtube.com/watch?v=8XPXW4s2iHU]("http://www.youtube.com/watch?v=8XPXW4s2iHU"). 

:guitar:

You could have LMMS on your system within 20 minutes, just from one command - this grabs LMMS from git and compiles it for you, no dependency hell here!:

> sudo aptitude update && sudo aptitude install libqt4-dev qt4-dev-tools git-core build-essential libsndfile1-dev libasound2-dev libjack0.100.0-dev libjackasyn-dev libsdl-sound1.2-dev  libsdl1.2-dev libsdl-mixer1.2-dev libvorbis-dev libvorbisfile3 libvorbisenc2 libsamplerate0-dev libstk0-dev stk libfftw3-dev libfluidsynth-dev git cmake && git clone git://lmms.git.sourceforge.net/gitroot/lmms && cd lmms && git checkout -b stable-0.4 origin/stable-0.4 && mkdir build && cd build && cmake .. -DCMAKE_INSTALL_PREFIX=/usr && make && sudo make install

---

### Post by decoherence on 2009-08-17
> **Mazza558 said:**
> Here's a video I made showing off what the free Linux synthesizer and sequencer, LMMS, can do. I can't stand people who say it's hard to make or produce music on Linux. With LMMS, it's easier than ever and certainly no harder than the lengths people sometimes have to go to get wifi or other drivers working on Ubuntu.

Either way, here's the video: [http://www.youtube.com/watch?v=8XPXW4s2iHU]("http://www.youtube.com/watch?v=8XPXW4s2iHU"). 

:guitar:

What I don't like about LMMS is that you can apply (for instance) C* AmpIII to each channel you want to, open up all their configuration windows and lose track of what window belongs to what channel. That's because the title of each of these configuration windows is called "C* AmpIII" rather than "Channel 1 - C*AmpIII" or some other distinguishable name.

This small oversight translated in to big frustration last time I tried to do anything serious with it. Being able to determine what effect goes with what channel at a glance is kind of a usability must-have. That said, in my frustration I gave up pretty quickly so if I'm missing something, please enlighten me and I'll give it another go!

---

### Post by Mazza558 on 2009-08-17
> **decoherence said:**
> What I don't like about LMMS is that you can apply (for instance) C* AmpIII to each channel you want to, open up all their configuration windows and lose track of what window belongs to what channel. That's because the title of each of these configuration windows is called "C* AmpIII" rather than "Channel 1 - C*AmpIII" or some other distinguishable name.

This small oversight translated in to big frustration last time I tried to do anything serious with it. Being able to determine what effect goes with what channel at a glance is kind of a usability must-have. That said, in my frustration I gave up pretty quickly so if I'm missing something, please enlighten me and I'll give it another go!

I'll ask the developers and see if this is going to be fixed. I can't say I've had such problems with effects, but that's because I use only a few tracks/channels to begin with.

---

### Post by Viva on 2009-08-17
Its refreshing to see a positive thread about ubuntu in the community cafe.

---

### Post by jerrrys on 2009-08-17
> **Viva said:**
> Its refreshing to see a positive thread about ubuntu in the community cafe.

yes, Im surprised how many look a gift horse in the mouth

---

### Post by cmay on 2009-08-17
when i used to do recording a lot i used this 
[http://www.64studio.com/](http://www.64studio.com/) which replaced rolands sonar and cubase. 

but now i sometimes just use audour and audacity on ubuntu to play with samples. i also use zynaddfx for my roland midi keyboard and hydrogen. its enough to play with as long as it is just for the fun of it. 

i would recommend all people that plays an instrument to look at the programs in ubuntu /debian for some free tools to record and make music.  there are a few but its free and some of them are actually great .

---

### Post by ibuclaw on 2009-08-17
What Soundcard/MIDI devices do you use?

I have actually considered giving EnergyXT a whirl too: [http://www.youtube.com/watch?v=g8Y6tOSV1MY](http://www.youtube.com/watch?v=g8Y6tOSV1MY)

Saw a review of it in SoundOnSound, it looked promising...

---

### Post by cmay on 2009-08-17
> **tinivole said:**
> What Soundcard/MIDI devices do you use?

I have actually considered giving EnergyXT a whirl too: [http://www.youtube.com/watch?v=g8Y6tOSV1MY](http://www.youtube.com/watch?v=g8Y6tOSV1MY)

Saw a review of it in SoundOnSound, it looked promising...

is program  this for linux ?  and can it be found in reposotories . 

btw:
i use the emu1212m soundcard. its a good soundcard for the prize i paid for it which was more than half the prize of . but its not suitable for someone who dont use midi firewire and since there is only one in /out analog which i use trough and old fostex eight track harddisk recorder. 

i use the midi instruments i have which is two drum machines and a roland midi keyboard. on linux in eihter 64studio or just ubuntu wiht the real time kernel installed.  i am not so happy wiht the soundcard but it was a cheap investment and i am only hobby songwriter. so its ok .

---

### Post by SunnyRabbiera on 2009-08-17
I rather like this creative song made with LMMS:
[http://www.youtube.com/watch?v=Bu9bQA-UKOU&feature=channel_page](http://www.youtube.com/watch?v=Bu9bQA-UKOU&feature=channel_page)

---

### Post by thisllub on 2009-08-17
I tried it out for the first time the other day.
Do you think it is better than Rosegarden?

I have an E403. Is that what you have there?

---

### Post by Grishka on 2009-08-17
there's [a lot of audio software for Linux](http://wiki.linuxaudio.org/wiki/start). getting the right hardware is the main problem now.

---

### Post by DeadSuperHero on 2009-08-17
Yeah. Until I can figure out how to get Audacity properly working with Pulse, I'm not going to be able to produce music easily. (Yes, I'm lame.)

Edit: Consequently, I also have to figure out how to get my Snowball USB microphone to work properly as well, it always records out of pitch.

---

### Post by Grishka on 2009-08-17
> **Mr. Psychopath said:**
> Yeah. Until I can figure out how to get Audacity properly working with Pulse, I'm not going to be able to produce music easily. (Yes, I'm lame.)

Edit: Consequently, I also have to figure out how to get my Snowball USB microphone to work properly as well, it always records out of pitch.

why not use JACK instead?

---

### Post by Warpnow on 2009-08-17
I spent a long time looking for a music program for linux I liked, but to be fair what I wanted was different than what most wanted. I didn't want to make impressive music, I wanted to make simple background music for videos I make.

Apple has garageband, and Windows has several different kinds. The applications are basically just dragging pre-recorded clips and instruments together on a timeline to make a decent little melody.

I couldn't find one then, but this was a couple years ago.

---

### Post by Mazza558 on 2009-08-17
> **Warpnow said:**
> I spent a long time looking for a music program for linux I liked, but to be fair what I wanted was different than what most wanted. I didn't want to make impressive music, I wanted to make simple background music for videos I make.

Apple has garageband, and Windows has several different kinds. **The applications are basically just dragging pre-recorded clips and instruments together on a timeline to make a decent little melody.**

I couldn't find one then, but this was a couple years ago.

LMMS can essentially do that easily - arranging samples. The problem is that it currently treats samples as instruments, so it's already set up for you to start "playing" that sample. 

> **thisllub said:**
> I tried it out for the first time the other day.
Do you think it is better than Rosegarden?

I have an E403. Is that what you have there?

I think it's the only usable Linux audio editor, the others don't offer the same combination of features.

I'm using an E-413 which is practically the same as your model.

---

