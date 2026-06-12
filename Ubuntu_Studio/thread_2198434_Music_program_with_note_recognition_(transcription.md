---
title: "Music program with note recognition (transcription)."
date: 2014-01-08
forum: Ubuntu Studio
---

### Post by bsyge11 on 2014-01-08
Hello I am looking for a program like audacious where you can plug your guitar in and play music and the musical notes will come up on the screen. There is a windows program called 12 notes that does this but I need one for Ubuntu. Do any exist? The term for the program is called transcription but I'm not sure if they're all the same. Thanks

---

### Post by bsyge11 on 2014-01-08
Or more importantly; which one or what program can I plug my guitar or mic into and have a live view of the notes and hopefully save sheet music of it:

 I am looking for a program like audacious where you can plug  your guitar in and play music and the musical notes will come up on the  screen. There is a windows program called 12 notes that does this but I  need one for Ubuntu. Do any exist? The term for the program is called  transcription but I'm not sure if they're all the same. Thanks

---

### Post by bsyge11 on 2014-01-08
I am looking for a program like audacious where you can plug  your guitar in and play music and the musical notes will come up on the  screen. There is a windows program called 12 notes that does this but I  need one for Ubuntu. Do any exist? The term for the program is called  transcription but I'm not sure if they're all the same. Thanks

---

### Post by Iowan on 2014-01-08
I have merged your three threads. Please read the [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):
> Do not cross post, or post the same thing in multiple locations.
You may use the Report Post button to have it moved to another forum, if necessary.

---

### Post by tgalati4 on 2014-01-09
There are a few tuner programs, that will give you the nearest note when a tone is played.  Don't know of any transcription programs.  There may be some on-line transcription, you would have to keep searching.  [http://customguitartabs.com/](http://customguitartabs.com/)

tgalati4@Mint14-Extensa ~ $ apt-cache search tuner
linux-firmware-nonfree - Non-free firmware for Linux kernel drivers
dov4l - program to set and query settings of video4linux devices
**fmit - Free Music Instrument Tuner**
fmtools - FM radio tuner
gkrellm-radio - FM radio tuner for GKrellM
gnomeradio - FM-radio tuner for the GNOME desktop
[B]gtkguitune - Guitar and other instruments tuner
gxtuner - Tuner for Jack[/B]
hdhomerun-config - Configuration utility for Silicon Dust HD HomeRun
hdhomerun-config-gui - GUI Configuration utility for Silicon Dust HD HomeRun
libhdhomerun-dev - Development library for Silicon Dust HD HomeRun
libhdhomerun1 - Library for Silicon Dust HD HomeRun
**lingot - accurate and easy to use musical instrument tuner**
mysqltuner - high-performance MySQL tuning script
nmon - performance monitoring tool for Linux
pgtune - PostgreSQL config tuner
**rakarrack - Simple and easy guitar effects processor for GNU/Linux**
streamtuner2 - Browser for Internet Radio Stations
**zita-at1 - JACK autotuner**

---

### Post by ian-weisser on 2014-01-09
Have you looked in Software Center?

Package *scolily*. I have not tried it.
> Description-en: Utility to create music scores from microphone
 Scolily record from any audio device handled by alsa,
 and then create a music score ( lilypond, ABC music
 and Midi files are currently supported ).

Another older -and still very good- way to do this was to use instruments that output in MIDI instead of using a microphone.
Microphones catch ambient noises that your brain ignores during the recording. That can lead to garbage in your transcription.
 Most good music notation software is MIDI-compatible.
That also means MIDI can be a useful filter for searches, even if you don't plan to use it.

---

### Post by zacktu on 2014-01-09
There's also denemo, which is in the Software Center.  It's not easy to install and has a rather steep learning curve.  It also uses lilypond, and the printed pages are as professional looking as any you will ever see.  I've used it before.

---

