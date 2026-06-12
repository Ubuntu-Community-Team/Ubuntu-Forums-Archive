---
title: "Any other CLI Music players?"
date: 2008-11-09
forum: The Cafe
---

### Post by blithen on 2008-11-09
I use CMUS religiously for my music playing, fast and snappy. But I was wondering if anyone else used a CLI music player, and if you use it for everyday use and how highly you would recommend it to someone.

---

### Post by EnGorDiaz on 2008-11-09
i use opencubic player thats great loads of customizeable options

---

### Post by blithen on 2008-11-09
> **EnGorDiaz said:**
> i use opencubic player thats great loads of customizable options

Holy crap! Thanks a lot, I will have to mess with this for a bit.

---

### Post by K.Mandla on 2008-11-09
cplay? mp3blaster? mpd and a frontend? alsaplayer and the text interface? 

You have a lot of options.

---

### Post by urukrama on 2008-11-09
Other than the ones mentioned, I also like mocp, and occasionally use just mpg123 without a frontend if I need to play a single file.

---

### Post by Nepherte on 2008-11-09
mpd + ncmpcpp.

---

### Post by blithen on 2008-11-09
> **Nepherte said:**
> mpd + ncmpcpp.
How did you get that to compile?

---

### Post by Rhubarb on 2008-11-09
Slightly off-topic, but I'm having troubles playing any sound from my Intrepid (8.10) server install. - there's no X installed, just bash.
It's not really important, but I'd like to be able to play a sound (not a beep from the PC speaker) whenever a specific event occurs on my server.
But I can't get any sounds out of it with ogg123 or aplay.

I have alsa-base alsa-utils libasound2 libasound2-plugins linux-sound-base installed.

**asoundconf list**
```
Names of available sound cards:
A5451
```

**lsmod | grep snd**
```
snd_ali5451            27532  0 
snd_ac97_codec        111652  1 snd_ali5451
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  3 snd_ali5451,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  10 snd_ali5451,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16136  1 snd_pcm
```

**sudo lspci -v**
```
00:04.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
	Subsystem: Fujitsu Limited. Device 1177
	Flags: bus master, medium devsel, latency 64, IRQ 9
	I/O ports at 1000 [size=256]
	Memory at e8101000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [dc] Power Management version 2
	Kernel driver in use: ALI 5451
	Kernel modules: snd-ali5451

```

When I try playing a sound file:
**ogg123 test.ogg**
```
Audio Device:   Advanced Linux Sound Architecture (ALSA) output

Playing: test.ogg
Ogg Vorbis stream: 2 channel, 44100 Hz
Artist: Daft Punk
Title: Harder, Better, Faster, Stronger
Album: Discovery
Genre: Electronic
Date: 2001
Track number: 4
ALSA lib confmisc.c:768:(parse_card) cannot find card 'A5451'
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1251:(snd_func_refer) error evaluating name
ALSA lib conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3985:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM default
ALSA snd_pcm_open error: No such device
Error: Cannot open device alsa.
```

But, if I run ogg123 test.ogg with sudo, it acts as if it's playing (but doesn't produce any audio).

I can't open up alsamixer unless I'm root either.

I have the linux-generic kernel installed (as the server kernel is incompatible with the 32bit Crusoe CPU on my server (an old laptop)).

Any help would be much appreciated.

---

### Post by ssam on 2008-11-09
mpd and xmms2 both have CLI clients.

---

### Post by urukrama on 2008-11-09
> **Rhubarb said:**
> Any help would be much appreciated.

Just start a thread about it in one of the support forums here.

---

### Post by brunovecchi on 2008-11-09
I use pyTone, does what I want and doesn't get in the way.

---

### Post by chucky chuckaluck on 2008-11-09
i just switched from cplay to cmus (for reasons that have nothing to do with either). cplay is great and so far, cmus looks great, as well. used to use mpd+ncmpc. it was great, too. i just found the initial configuration mysteries intensely annoying. never could figure out mp3blaster.

---

### Post by billgoldberg on 2008-11-09
> **blithen said:**
> I use CMUS religiously for my music playing, fast and snappy. But I was wondering if anyone else used a CLI music player, and if you use it for everyday use and how highly you would recommend it to someone.

I used mpd + mpc on fluxbox.

It was great.

---

### Post by elmer_42 on 2008-11-09
> **Nepherte said:**
> mpd + ncmpcpp
This is also what I use to listen to music. Luckily it was in the Arch Users' Repository, so compiling it was easy.

---

### Post by Nepherte on 2008-11-09
> **elmer_42 said:**
> This is also what I use to listen to music. Luckily it was in the Arch Users' Repository, so compiling it was easy.
Same here, I use Arch.

> **blithen said:**
> How did you get that to compile?
As far as I can remember, mpd is in the ubuntu repositories. To compile ncmpcpp, I suggest you take a look at [http://unkart.ovh.org/ncmpcpp/download.php#others](http://unkart.ovh.org/ncmpcpp/download.php#others)

---

### Post by chris4585 on 2008-11-09
mocp is great, and heres one no one has mentioned yet, randomplay

---

### Post by EnGorDiaz on 2008-11-23
> **blithen said:**
> Holy crap! Thanks a lot, I will have to mess with this for a bit.

its great its really worth trying

---

### Post by bobbocanfly on 2008-11-23
1 vote for mpd + ncmpc + mpdscribble (Last.fm plugin for MPD) (the C version, not ncmpcpp). After setting it all up (including some shiny cron jobs to update the database every hour) it is working brilliantly.

---

### Post by zmjjmz on 2008-11-23
> **EnGorDiaz said:**
> its great its really worth trying

Really, really dumb question, but how do you launch it?
EDIT: That was so dumb. It's ocp

---

### Post by chris4585 on 2008-11-23
> **zmjjmz said:**
> Really, really dumb question, but how do you launch it?
EDIT: That was so dumb. It's ocp

nah, when someone mentions moc they should always mention that the binary is mocp...

---

