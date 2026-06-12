---
title: "Audio...."
date: 2008-11-19
forum: Server Platforms
---

### Post by Andrew Borem on 2008-11-19
I have an interesting desire, and I am not sure how to make it happen.

My wife recently got a job and is working on a website for the company.  So we got a cheap computer and I set it up as a lamp server with bind and webmin and stuff.  Now, the problem I am having is that I have all kinds of wasted computer, and the nerd I am, I want to make it do more.

I am running ubuntu server edition i386 8.10

I don't want to install X at all.  What I want to do is find and install a terminal based media player.  The audio driver works in ubuntu, so I just need something to output sound.  I am not a linux novice, nor am I a master.  Just assume I know how to google things if there is something I don't understand.

I can't seem to find anything like this on google, but that is possibly because I don't know what to google for.  Could anyone help me out here?

---

### Post by cdenley on 2008-11-19
```

sudo apt-get install mplayer

```

---

### Post by Andrew Borem on 2008-11-19
> **cdenley said:**
> ```

sudo apt-get install mplayer

```

```
AO: [pulse] Failed to connect to server: Connection refused
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA] alsa-lib: conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM default
[AO_ALSA] Playback open error: No such file or directory
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA] alsa-lib: conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM default
[AO_ALSA] Playback open error: No such file or directory
[AO ARTS] loading the aRts backend "/usr/lib/libartscbackend.la" failed
[AO ESD] esd_open_sound failed: Connection timed out
AO: [pulse] Failed to connect to server: Connection refused
[JACK] cannot open server
ao_nas: init(): AUDIOSERVER environment variable not set -> nosound
[AO SDL] Samplerate: 44100Hz Channels: Stereo Format s16le
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA] alsa-lib: conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM default
[AO SDL] Unable to open audio: No available audio device
AL lib: alsa.c:784: no playback cards found...
AL lib: alsa.c:852: no capture cards found...
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA] alsa-lib: conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM default
[AO_ALSA] alsa-lib: confmisc.c:768:(parse_card) cannot find card '0'
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_card_driver returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:392:(snd_func_concat) error evaluating strings
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_concat returned error: No such file or directory
[AO_ALSA] alsa-lib: confmisc.c:1251:(snd_func_refer) error evaluating name
[AO_ALSA] alsa-lib: conf.c:3513:(_snd_config_evaluate) function snd_func_refer returned error: No such file or directory
[AO_ALSA] alsa-lib: conf.c:3985:(snd_config_expand) Evaluate error: No such file or directory
[AO_ALSA] alsa-lib: pcm.c:2196:(snd_pcm_open_noupdate) Unknown PCM default
AL lib: alsa.c:344: Could not open playback device 'default': No such file or directory
AL lib: oss.c:179: Could not open /dev/dsp: No such file or directory
[OpenAL] could not open device
Opening /dev/dvb/adapter0/audio0
DVB AUDIO DEVICE: No such file or directory
AO: [null] 44100Hz 2ch s16le (2 bytes per sample)

```

Do you know what that noise is all about?  I am going to google for the solution, but I just wanted to post this first to expedite a response if I don't find one on google.

Thank you.

I have an nvidia mcp61 chipset, by the way.  the onboard ethernet works great, and as I stated before, it worked in desktop.  LSPCI shows it, as well.  Is it possible that it is disabled?

Also, here is the lshw of the sound:

```

     *-multimedia
          description: Audio device
          product: MCP61 High Definition Audio
          vendor: nVidia Corporation
          physical id: 5
          bus info: pci@0000:00:05.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pm msi ht bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel

```

Thanks for the help, guys.  I figured it out.  I built a new driver from source with the latest from the devs over at alsa, and that seemed to take care of it.  So great.

---

