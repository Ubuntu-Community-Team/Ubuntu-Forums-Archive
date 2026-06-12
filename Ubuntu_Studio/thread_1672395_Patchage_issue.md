---
title: "Patchage issue"
date: 2011-01-20
forum: Ubuntu Studio
---

### Post by sevenenemy on 2011-01-20
got ubuntu studio packages lastnite and i am very impressed, a little bummed i cannot get the PPA's resolved for the graphics portion but thats for another post as it seems to be a known issue. i started fast, ripped some cds using ripoff, converted them to mp3's, (on a side note, would be helpful to know what the variables are for ripping straight to mp3 from rippoff, i have the lame mp3 plugin that goes with it and i dont understand what value to put in the track output values field to make it an mp3, i have to rip it and then convert it to mp3 using sound converter) fiddled around online trying to set up my mic's as they were not working at all but i figured it all out and then started recording. all was going well and i decided to start playing with stuff. long story short i was in patchage, and there were some green boxes for midi things, i left those alone, i could not make any connections to those, but i did connect the blue inputs to the blue outputs, saved, and closed. i dont know why i did this, i guess i am just destructive. it messed up my whole recording environment. eventually after changing things inside audacity preferences i got it to record again, and with the damage done and assumed fixed i went to bed before i broke something else. so today i ripped some more cd's and went to do a bulk convert, and i get the following error on every file it tries to convert. "GSTreamer error when creating pipeline. could not link audioconvert1 to lame0" it is worth noting that after i messed with patchage and broke the recording link, audacity would stay stuck at 00.00 playtime when i pressed record and give me an error about latency being reset to zero, and also in audacity under preferences > devices > my sound card or alsa mixer or whatever my output was (i dont remember exactly what it was labeled, just that it was the device name for my sound card or mixer or what have you, im new to all this please bear with me) is no longer shown in the menu, although i can still get sound output in all programs, games, you name it, by setting the playback device's drop-down menu to default. so i can actually still use what i have now to tinker with recording and still listen to music and play and have fun and all good things, but i cannot convert sound files which i am in need of being able to do. to recap if you are still with me after all this reading i assume this is all to do with linking my inputs to my outputs, both boxes blue, each with two channels or whatever they were, if you know patchage you should know what i am talking about, and the real problem here is that when i open patchage to correct the problem, those two blue boxes, one for input, one for output, which i linked together to their corresponding channels, are no longer visible! all i did in patchage was link the two channels in the blue boxes together and save thinking that would do something nice and when it broke and i tried to fix it they were gone. NO BLUE BOXES! is there a reset to default command? maybe some -RF type ****! please help thanks, and thanks for bearing with me.
Hunter

---

### Post by sgx on 2011-01-21
Hi, I would ignore patchage for what you are doing, and go here

[http://www.liberiangeek.net/2010/07/quickly-convert-audio-cd-mp3-wav-ogg-flac-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/07/quickly-convert-audio-cd-mp3-wav-ogg-flac-ubuntu-10-04-lucid-lynx/)

There are screengrabs of the gui in each phase of the rip/convert process.

Then, I would set aside a couple hours to study ffmpeg, a universal stalwart, which you can use to do almost anything.

type man ffmpeg

if it is installed, you'll see a long list of options and examples
that you can craft to meet your needs. To install it, check in th repositories synaptic package manager to find, along with transcode, win32codecsall, and a raft of gstreamer codecs.
There also are several other concertor apps available in the repositories.

Patchage is more useful for connecting midi instruments and midi/audio inputs/outputs to each other.

Cheers

---

### Post by Pablo_F on 2011-01-21
Hi,

To make things short, maybe too short, in ubuntustudio  there are two "sound systems" or sound servers. One of them is jack and the other is pulseaudio. 

Pulseaudio is the default and it is oriented to desktop use. You control pulsaudio by means of the sound preferences. (Or pavucontrol, which is similar but not installed by default I think)

Jack is oriented to music production.

Basically, when pulseaudio is up and running, only "pulseaudio-aware" applications will playback or capture sound. When jack is running only jack-aware apps will capture or playback sound. 

Patchage is used to make audio connections between jack clients (basically, jack-aware applications and audio card), the blue boxes and lines are jack audio. Patchage can be also used to make MIDI connections. The green boxes are alsa MIDI clients. If you see blue boxes in patchage, jack is running.

As mentioned above, if jack is running you only get audio from jack-aware apps AND some jack-aware applications launch the jack server on the background.

If jack is running Sound Preferences will fail. If you did nothing to "jackify" gstreamer, gstreamer will fail too. 

If you don't intend to make music with your computer, you can safely remove jackd and whatever package which depends on jackd. 

Cheers! Pablo

---

### Post by sevenenemy on 2011-01-21
i intend to make music pablo, so i would like to figure out what i did and how i can fix it and keep jack, i might have made the first post too long, quick breakdown.

beginning of the day after ubuntu studio install... all was well

middle of the day ... had been ripping and converting cds to mp3, sgx pointed me to a better ripper today that converts straight to mp3 which removes a step for me. 

shortly after i finished my rip/converts i made the connections, two jack connections labelled 1 and 2 or 0 and 1 cant remember, for input, and identical for output, i connected the corresponding numbered inputs to the outputs, and that gave me the gstreamer error when converting, also it removed my playback device from the preferences of audacity.

everything worked until i made those connections, and while i did get it all working again by selecting default device in preferences > playback, and manipulating a few other minor settings, i would like to get it back to where it should be.

i am going to try to open a jack app and see if i can get patchage to show those connections so i can unlink them, that should fix it.

will re post shortly with solved or further AHHHHHHHHHH HEEEELP MEEEE!

hunter

---

### Post by sevenenemy on 2011-01-21
ok so here is the cry for help as promised!

it appears i cannot open any jack application period. anyone reading this post DO NOT CONNECT JACK INPUTS STRAIGHT TO OUTPUTS IN PATCHAGE UNLESS YOU KNOW WHAT YOU ARE DOING!

what now? eeep.

---

### Post by sevenenemy on 2011-01-21
if this helps sort it out the error i am getting from converting audio files after all this is "GSTreamer error when creating pipeline could not link audioconvert1 to lame0" i linked these i presume and it cannot do this apparently??

on a side note audio DOES convert i just get this error on every file, if needed i can post links to the other threads with information pertaining to this mess for anyone who is reading that might be able to help but is not following.

also ive moved away from the converting issue and have focused on the patchage issue, for that is what started the whole mess

---

### Post by sgx on 2011-01-21
[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

you can try this link, screengrabs showing connections
between jackd and the softsynth zynaddsubfx using qjackctl

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)  

there are more good links here
for different takes on jackd connections, and youtube videos about
Ardour and Hydrogen will often include qjackctl connections, since they
occur first in the recording setup.

Cheers

---

### Post by sevenenemy on 2011-01-22
when i try to set it up this way i do not see anything in the audio tab at the top of jack controls connection window, all i see when i open these apps are in the alsa tab, it all goes back to making the connections in patchage, I NEED A TERMINAL DEFAULT SETTING GAAAH WHYYYYYYY MEEEE, lol. rant off. on a plus side at least i can still record at the moment with what i have.

---

### Post by sgx on 2011-01-22
> **sevenenemy said:**
> when i try to set it up this way i do not see anything in the audio tab at the top of jack controls connection window, all i see when i open these apps are in the alsa tab, it all goes back to making the connections in patchage, I NEED A TERMINAL DEFAULT SETTING GAAAH WHYYYYYYY MEEEE, lol. rant off. on a plus side at least i can still record at the moment with what i have.

Stop the jackd in qjackctl, (restarting is required for all changes to take effect) and in the setup page of qjackctl, middle right

Input Device >
Output Device >

click the > widgets to choose from your available soundcards/chips.
Restart jackd from qjackctl, and check the audio and alsa tabs.

Post what is shown in the > widgets, and the sound portion from the output
of the lsmod command. Something from the widgets should show up in that output (it just list kernel modules, my lsmod contains these:

snd_seq_oss            22774  0 
snd_seq_midi_event      5464  2 snd_seq_midi,snd_seq_oss
snd_seq                40753  9 snd_seq_midi,snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
snd_seq_device          5214  5 snd_seq_midi,snd_rawmidi,snd_seq_dummy,snd_seq_oss,snd_seqsnd_seq_oss            22774  0 
snd_seq_midi_event      5464  2 snd_seq_midi,snd_seq_oss
snd_seq                40753  9 snd_seq_midi,snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
snd_seq_device          5214  5 snd_seq_midi,snd_rawmidi,snd_seq_dummy,snd_seq_oss,snd_seq
snd_pcm_oss            29040  0 
snd_pcm                58856  6 snd_usb_audio,snd_ice1712,snd_ac97_codec,snd_pcm_oss
snd_timer              15794  2 snd_seq,snd_pcm
snd_page_alloc          6506  1 snd_pcm
snd_mixer_oss          11096  1 snd_pcm_oss
snd                    46351  28 snd_usb_audio,snd_hwdep,snd_usb_lib,snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_i2c,snd_mpu401_uart,snd_rawmidi,snd_seq_oss,snd_seq,snd_seq_device,snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss

My > widgets each have

hw:0,0 snd_ice1712
hw:0 M Audio Audiophile 24/96

If you have a usb soundcard the setup page has a periods/buffers setting
that should be 3

if your soundchip is part of a newer videocard, it may not be properly supported yet.

jackd -dalsa -r44100

will start jackd, you can start qjackctl second.

Cheers

---

### Post by sevenenemy on 2011-01-23
i dont think youre getting it i cant open ANYTHING related to jack because of the link i made in patchage.

this is the error i get from running the last command you suggested in terminal

hunter@hunter-Extensa-5420:~$ jackd -dalsa -r44100
jackdmp 1.9.6
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
no message buffer overruns
no message buffer overruns
JACK server starting in realtime mode with priority 10
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xf0700000 irq 16
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
Cannot initialize driver
JackServer::Open() failed with -1
Failed to start server
hunter@hunter-Extensa-5420:~$ 

whatever i linked in patchage is the only problem i am having at this point and that is what i need to fix before i can do anything more. 

sorry if i seem "short" at the top but it is looking like the best course of action is a full system wipe and i will start all over and leave it all alone, at least that way anything else i have changed will be fixed, but regardless its still frustrating.

thanks,
hunter.

---

### Post by Pablo_F on 2011-01-23
Hi,

EDIT: 

use the command:

lsof /dev/snd/pcmC0D0p

to see what process is using the audio card

Then do a:

kill PID

where PID is the PID (process ID) number 

I think this is a better idea than I posted earlier, which was:

Try reloading the alsa modules with the command:

sudo alsa force-reload

and see if jackd starts now.

Cheers, Pablo

EDIT:

---

### Post by sgx on 2011-01-23
Whats in the > widgets in qjackctl?

What devices are plugged in to usb ports? or other misc devices?
If some internet doohickey is active at bootime, it may grab your sound
before you start anything.

what is output of  lsmod ?

what is output of

cat /proc/asound/cards /proc/asound/pcm

my output from the above is

 0 [M2496          ]: ICE1712 - M Audio Audiophile 24/96
                      M Audio Audiophile 24/96 at 0xac00, irq 17
00-00: ICE1712 multi : ICE1712 multi : playback 1 : capture 1

My  > widgets have 

hw:0,0 snd_ice1712
hw:0 M Audio Audiophile 24/96

lsmod output includes   snd_ice1712

The common denominator, is ice1712, the soundchip on my soundcard.
You may have more than 1, and the wrong one might be used, so these outputs will help enlighten us, (yeah, its mainly Greek to me too ;)

this is my .jackdrc file:

/usr/bin/jackd -P89 -t2000 -u -dalsa -r44100 -p256 -n4 -D -Chw:0,0 -Phw:0,0 -s

yours will be different, but post it

Chw:0,0  =capture hardware 0,0

Phw:0,0 =playback hardware 0,0   these are your sound input and outputs.

We can connect the dots if we have them.

From your jackd error output:

Using ALSA driver HDA-Intel running on card 0 - HDA ATI SB at 0xf0700000 irq 16
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again

something is getting to hw:0 before you are!  In the meantime,

try this, reboot, issue the command

killall pulseaudio

then

jackd -dalsa -r44100  looks a bit like this when it works:

loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 44100Hz, period = 1024 frames (23.2 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback

Cheers :)

---

### Post by sevenenemy on 2011-01-29
turns out its fixed after a wipe and fresh install of ultimate edition thrillseekers unite. i linked the jack system captures to the system playbacks and i suggest people refrain from doing this. 8) solved

---

### Post by sevenenemy on 2011-01-29
oh and thanks guys i didnt see there was a second page to this if anyone does this make sure to just do a fresh install of ubuntu ultimate edition and ignore the previous three posts! just kidding no seriously try those steps first or dont do this.

---

