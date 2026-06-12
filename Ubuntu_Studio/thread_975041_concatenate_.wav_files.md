---
title: "concatenate .wav files?"
date: 2008-11-08
forum: Ubuntu Studio
---

### Post by pmooney78 on 2008-11-08
Is there any easy way to concatenate .wav files? I've tried using sox to do so, i.e. 

sox 01\ -\ Richard\ Strauss\ -\ Wie\ schon\ ist\ die\ Prinzessin\ Salome.wav 02\ -\ Richard\ Strauss\ -\ Nach\ mir\ wird\ Einer\ kommen.wav concat.wav

and get

sox soxio: Failed reading `02 - Richard Strauss - Nach mir wird Einer kommen.wav': unknown file type `auto'

just typing "sox" gets this at the end:

SUPPORTED FILE FORMATS: m3u pls

SUPPORTED EFFECTS: allpass band bandpass bandreject bass chorus compand dcshift deemph dither earwax echo echos equalizer fade filter flanger highpass key ladspa lowpass mcompand mixer noiseprof noisered oops pad pan phaser polyphase rabbit repeat resample reverb reverse silence speed stat swap synth tempo treble tremolo trim vol

effopts: depends on effect

WTF? Sox claims to be able to support all types of audio files, including .wav. Why is it claiming it can only play .m3u and .pls?

Is there a good way to fix this? Or another easy way to concatenate .wav files from the command line? (Sure, I can use any number of graphical tools, but I like the "specify the options and let it run in the background" nature of command-line options.)

Come to think of it, is there a way to concatenate aac files from the command line? (Especially without decompressing/recompressing, as the sox manual suggests will happen?)

Thanks in advance for any help. If it's relevant, I'm running Xubuntu 8.04 on a Pentium III 550 MHz with 384 megabytes of RAM.

---

### Post by ad_267 on 2008-11-08
sudo apt-get install libsox-fmt-all

That should install support for all the formats.

---

### Post by Stochastic on 2008-11-08
You could also use ecasound, but I don't recall the exact commandline options off the top of my head.

---

### Post by andrew.46 on 2008-11-11
Hi,

I am not on my Ubuntu partition at the moment but as ad_267 has suggested I suspect you only have part of SoX installed. I have just finished compiling the newest version:

```
andrew@skamandros~$ sox --version
sox: SoX v14.2.0
```

and supported audio formats is pretty huge:

```
andrew@skamandros~$ sox | grep 'AUDIO FILE FORMATS:'
Failed: Not enough input filenames specified

AUDIO FILE FORMATS: 8svx aif aifc aiff aiffc al amb amr-nb amr-wb anb au 
avr awb cdda cdr cvs cvsd dat dvms f4 f8 flac fssd gsm hcom htk ima ircam 
la lpc lpc10 lu maud mp2 mp3 nist ogg prc raw s1 s2 s3 s4 sb sf sl smp snd 
sndr sndt sou sox sph sw txw u1 u2 u3 u4 ub ul uw vms voc vorbis vox wav
wavpcm wv wve xa
```

  Andrew

---

### Post by pmooney78 on 2008-11-21
Installing soxfmt-all fixes the problem. Thank you!

---

### Post by cotcot on 2008-11-22
```
cat audio1.wav audio2.wav audio3.wav > audio.wav
```

---

### Post by Stochastic on 2008-11-22
> **cotcot said:**
> ```
cat audio1.wav audio2.wav audio3.wav > audio.wav
```
NO.

NO.

WRONG.
Cat simply puts the data in each file back-to-back into a new file.  Audio has headers that need editing/adjusting etc.. cat doesn't work with audio well.  It should only be used when there is no other alternative.  Sox is a much better solution.

---

