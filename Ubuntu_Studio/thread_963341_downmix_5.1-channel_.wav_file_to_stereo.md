---
title: "downmix 5.1-channel .wav file to stereo"
date: 2008-10-30
forum: Ubuntu Studio
---

### Post by pmooney78 on 2008-10-30
I've got a 5.1-channel .wav file (dumped from a DVD with VLC's transcode wizard) that I'd like to downmix to stereo so I can convert it to .mp3. What's the easiest way to do this? I'd prefer a command-line program if possible.

If it's relevant, I'm running Xubuntu 8.10 on a Pentium III 550 MHz with 384 Mb of RAM.

---

### Post by FakeOutdoorsman on 2008-11-01
I have no experience with 5.1 channel wav, but I'm guessing ffmpeg should be able to do this:
```
ffmpeg -i input.wav -ac 2 -ab 128k output.mp3
```
If that doesn't work, then paste the complete ffmpeg output of that command.

---

### Post by Stochastic on 2008-11-02
It should be noted that there are potential major issues with a downmix.  If the sounds are at all spatialized (time differences, reverb, etc...), then mixing two channels together into one is going to give a comb filter effect, phasing distortion, and other artifacts.  What I would do is use the LADSPA ambisonic encoder/decoder plugin set to encode the file from a 5.1 to a B-Format then decode from B-Format to stereo (this should all be doable through an ardour effects chain - or maybe even a jack rack effects chain).  I'd be extremely surprised if ffmpeg took into account any spatial cue artifacts when mixing down.

---

### Post by pmooney78 on 2008-11-07
> **FakeOutdoorsman said:**
> I have no experience with 5.1 channel wav, but I'm guessing ffmpeg should be able to do this:
```
ffmpeg -i input.wav -ac 2 -ab 128k output.mp3
```
If that doesn't work, then paste the complete ffmpeg output of that command.

Doesn't work. I get this:

```

patrick@liniscient:/media/Docs/My Documents$ ffmpeg -i "baby i love you.wav" -ac 2 -ab 128k "baby i love you.mp3"
FFmpeg version SVN-rUNKNOWN, Copyright (c) 2000-2007 Fabrice Bellard, et al.
  configuration: --enable-gpl --enable-pp --enable-swscaler --enable-pthreads --enable-libvorbis --enable-libtheora --enable-libogg --enable-libgsm --enable-dc1394 --disable-debug --enable-shared --prefix=/usr
  libavutil version: 1d.49.3.0
  libavcodec version: 1d.51.38.0
  libavformat version: 1d.51.10.0
  built on Jul 23 2008 22:38:24, gcc: 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
Input #0, wav, from 'baby i love you.wav':
  Duration: 00:05:04.8, start: 0.000000, bitrate: 4607 kb/s
  Stream #0.0: Audio: pcm_s16le, 48000 Hz, 5:1, 4608 kb/s
Resampling with input channels greater than 2 unsupported.Can't resample.  Aborting.
Abort at ffmpeg.c:1573
Aborted

```

Any suggestions appreciated.

---

### Post by pmooney78 on 2008-11-07
> **Stochastic said:**
> It should be noted that there are potential major issues with a downmix.  If the sounds are at all spatialized (time differences, reverb, etc...), then mixing two channels together into one is going to give a comb filter effect, phasing distortion, and other artifacts.  What I would do is use the LADSPA ambisonic encoder/decoder plugin set to encode the file from a 5.1 to a B-Format then decode from B-Format to stereo (this should all be doable through an ardour effects chain - or maybe even a jack rack effects chain).  I'd be extremely surprised if ffmpeg took into account any spatial cue artifacts when mixing down.

Sorry, way over my head. I'm a newbie. I do understand the issues involved, byt can't interpret the suggestions.

Can you post a code snippet?

---

### Post by Stochastic on 2008-11-07
My suggestion is done in a GUI so a code snippet wouldn't be of any help.  It would merely look like ```
ardour
```
Take a read through some tutorials on how to use plugins in Ardour and this may become clearer.

---

### Post by pmooney78 on 2008-11-08
> **Stochastic said:**
> My suggestion is done in a GUI so a code snippet wouldn't be of any help.  It would merely look like ```
ardour
```
Take a read through some tutorials on how to use plugins in Ardour and this may become clearer.

Can you point me towards useful tutorials? A quick google search hasn't turned up anything useful.

Thank you.

---

### Post by Stochastic on 2008-11-08
This tutorial (the first result in google on an "ardour tutorial" search) is quite good at explaining ardour to beginners: [http://www.out-of-order.ca/tutorials/ardour/](http://www.out-of-order.ca/tutorials/ardour/)

On top of that, then you'll need to download the CMT (computer music toolkit) ladspa plugins ```
sudo apt-get install cmt
```

Then it's just a matter of setting up the ambisonic encode and decode plugins in the right way to downmix the file to stereo.  I don't see any tutorials anywhere on this, so you may get confused, but it is somewhat self explanatory in the GUI of the plugins.

You may need to setup an external recording tool (i.e. a wave editor such as audacity, rezound, snd, ecasound, etc...) to grab the stereo output of the decoder plugin, if the audacity session is all in multi-channel format, though I'd need to give things a try to fully recall (this would be done by routing through the qjackctl patchbay).

You might also need to give a read on qjackctl basics before attempting this: [https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)
[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

---

### Post by pmooney78 on 2008-11-21
Yipes. I'm grateful for the input, but too steep a learning curve for me. I got it done with Audacity, with no unpleasant artifacts.

---

