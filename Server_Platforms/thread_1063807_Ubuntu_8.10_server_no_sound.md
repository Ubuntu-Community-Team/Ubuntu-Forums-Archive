---
title: "Ubuntu 8.10 server no sound"
date: 2009-02-08
forum: Server Platforms
---

### Post by krak on 2009-02-08
After installing ubuntu 8.10 server and fluxbox I found out there is no sound. A search forum but i could not find any solution sound still does not work.

I installed the following packages

alsa-base
alsa-utils
linux-sound-base

```
asoudconf list
```

```
I82801DBICH4
```

```
asoundconf set-default-card I82801DBICH4
```

Still no sound.

---

### Post by linux_tech on 2009-02-08
what is output of 
 ```

cat /proc/asound/card0/codec#* | grep Codec
aplay -l 
```

What make/model is this?  What sound card or chip?

---

### Post by krak on 2009-02-08
```
cat /proc/asound/card0/codec#* | grep Codec
```
```
cat: /proc/asound/card0/codec#*: No such file or directory
```

```
aplay -l
```
```
aplay: device_list:215: no soundcards found...
```


```
 cat /proc/asound/cards 
```
```
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with AD1981B at irq 11

```


```
lsmod | grep snd
```
```
snd_intel8x0           37532  0 
snd_ac97_codec        110372  1 snd_intel8x0
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46720  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83332  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            38400  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29832  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    63268  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
snd_page_alloc         16264  2 snd_intel8x0,snd_pcm

```

I'm running Ubuntu on IBM R40 notebook. On Ubuntu desktop sound works fine no configuration needed.

---

### Post by skunkbad on 2009-02-08
What sounds would you hear on Ubuntu server? I've never heard any. I don't really need to hear any, but wondering.

---

### Post by volkswagner on 2009-02-08
> **skunkbad said:**
> What sounds would you hear on Ubuntu server? I've never heard any. I don't really need to hear any, but wondering.

I am not sure what the OP wants to hear.  I personally am following this thread, as I would like to hear music.

I am trying to get Jinzora to play locally to Audio rack.  This would give me a web interface based whole house jukebox.

I have a thread started in [hardware]("http://ubuntuforums.org/showthread.php?t=1060120").  I seem to be a good thread killer.

I also posted in [other OS talk]("http://ubuntuforums.org/showthread.php?t=1060363") since I got sound working OTB with Slax5 live CD.

Sorry, I couldn't help myself.  :)

---

### Post by cariboo on 2009-02-08
It is pretty easy to get sound working on a server if you don't start adding gui elements, that just makes it more complicated. I use a headless emachine to play music in my shop. All I had to do was install alsa-base and alsa-utils start alsamixer turn up the volume and start playing tunes. I am using an Ensoniq1371. I also have had other sound cards installed and they worked just as well, the only one I had problems with was an AU8880, the drew more amps then the power supply could produce. :)

I use randomplay and mpg123 for playback

Jim

---

### Post by kindofabuzz on 2009-02-09
yeah why are you even running a desktop on a server? that's what the desktop edition is for. And to the person above running jinzora, the purpose of that is to stream music. You just point your browser to the name of the server. you don't listen to it from the server itself.

---

### Post by volkswagner on 2009-02-09
> **kindofabuzz said:**
> yeah why are you even running a desktop on a server? that's what the desktop edition is for. And to the person above running jinzora, the purpose of that is to stream music. You just point your browser to the name of the server. you don't listen to it from the server itself.

Actually Jinzora has a cool feature to allow local playback.  Jukebox mode is what I am after.  This would give all family members control over the whole house sound on each of their laptops.

[QUOTE=From_Jinzora_Site]
Jukebox Mode

Maarten Holland

05/07/2008 03:15 pm

In Jukebox Mode, Jinzora provides an interactive method to control a multimedia player.

This is a two-way mode: Jinzora interacts with a hard- or software media player, allowing the end-user to control the player from within the Jinzora interface.

The available controls vary, depending on the player of choice, but all players support at least the basic options of starting a track, pausing and stopping it, and changing tracks. This is a great way to control multiple players in a network from one single Jinzora interface.

Jukebox Mode works with three types of players: Command line players that are available on the Jinzora server, desktop players on the visiting client and even dedicated hardware devices!
[/QUOTE]

---

