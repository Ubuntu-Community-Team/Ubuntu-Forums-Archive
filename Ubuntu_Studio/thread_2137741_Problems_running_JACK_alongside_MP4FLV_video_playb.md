---
title: "Problems running JACK alongside MP4/FLV video playback"
date: 2013-04-21
forum: Ubuntu Studio
---

### Post by Koori Graywolf on 2013-04-21
I'm being unable to have Qjackctl running and play videos at the same time (Ubuntu Studio 12.10). If I run and Start JACK right after signing in to Ubuntu Studio it'll start successfully. However, if at any point I watch a video on Firefox, or load an MP4 or FLV video on the default Movie Player, I won't be able to Start the JACK server afterwards, even if I close the movie player or the web browser (I have to log out and log back in).

Also, if I'm running JACK and then try to play a video, they freeze (without any audio) and don't play at all.

Initially, I wasn't even able to play music on Audacious while running JACK (just loading Qjackctl is no problem, my issues are once I hit "Start"), but I found out by changing the output to JACK it'll work. Still, it's annoying because if I'm running Jack, I need to change Audacious' output, then if I close JACK, Audacious crashes. If anyone can help me with that that would be great, but my main issue is with JACK + playing videos.

This is what I get on Qjackctl:

 > Cannot connect to server socket err = No such file or directory

 Cannot connect to server request channel
 jack server is not running or cannot be started

[COLOR=#ff0000]16:45:08.870 D-BUS: JACK server could not be started. Sorry[/COLOR] Cannot connect to server socket err = No such file or directory
 Cannot connect to server request channel
 jack server is not running or cannot be started
 Sun Apr 21 16:45:08 2013: Starting jack server...
 Sun Apr 21 16:45:08 2013: JACK server starting in non-realtime mode

 Sun Apr 21 16:45:08 2013: control device hw:0

 Sun Apr 21 16:45:08 2013: control device hw:0
 Sun Apr 21 16:45:08 2013: Acquired audio card Audio0
 Sun Apr 21 16:45:08 2013: creating alsa driver ... hw:0|hw:0|1024|3|44100|0|0|nomon|swmeter|-|16bit
 Sun Apr 21 16:45:08 2013: control device hw:0
 Sun Apr 21 16:45:08 2013: [1m[31mERROR: 
 ATTENTION: The playback device "hw:0" is already in use. The following applications  are using your soundcard(s) so you should  check them and stop them as necessary before  trying to start JACK again:
 pulseaudio (process ID 1854)
 [0m
 Sun Apr 21 16:45:08 2013: [1m[31mERROR: Cannot initialize driver[0m
 Sun Apr 21 16:45:08 2013: [1m[31mERROR: JackServer::Open failed with -1[0m
 Sun Apr 21 16:45:08 2013: [1m[31mERROR: Failed to open server[0m
 Sun Apr 21 16:45:09 2013: Saving settings to "/home/koori/.config/jack/conf.xml" ...
 [COLOR=#ff0000]16:45:11.026 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

I've already tried:
- Searching for "Jack server could not be started. Sorry" issues on the web
- Reading: [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)
- Disabling realtime
- Forcing 16 bit
- Setting memlock in */etc/security/limits.d/audio.conf *to half my RAM
- Adding myself to the audio group
- Searching the forum for JACK + video playback-related issues

Please consider that I'm pretty much an Ubuntu newbie. Thank you very much!

EDIT: I found this website [https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro) and checked "The Pulse Audio to Jack Bridge - using both at once" to see if that could solve the issue, but I can't make Jack Sink and Jack Source on the connections window...

---

### Post by jejeman on 2013-04-22
After playing a video, reset pulseaudio
```
pulseaudio -k
```
Try then to start JACK.
JACK is not casual. It is a dedicated tool used to do the job. So, use it only when you have to do audio production tasks. VLC has jack output, try it.
Of course you can set JACK to be active all the time and handle all the audio, but I don't know if that is good idea.

---

### Post by Koori Graywolf on 2013-04-22
Thanks for your reply Jejeman.

Yeah, I initially did not think of using JACK while doing other  multimedia stuff. This occasion is specifically because I want to check  an Ardour tutorial video, but Ardour requires me to have JACK running,  so I can't watch the video while following the instructions.

It is a somewhat long video so I'm trying to avoid having to watch the  video, then run jack, run Ardour, follow the steps I can remember, turn  off jack, watch another video portion, turn on JACK and run Ardour  again, and so on.

I've searched some more and I see it is possible to route PulseAudio to  Jack. However, I've followed a lot of custom startup scripts added to  the system settings or to JACK's "Execute pre startup", "Execute post  startup", etc., and no matter what I do I can't make pulse audio sink  and source appear on JACK's connection window. I already have  pulseaudio-module-jack.

I will try using VLC later 'cause right now I don't have any more time, but if it has JACK output then I should have absolutely no problem.

Thank you for your help.

---

### Post by jejeman on 2013-04-22
Forget about pulseaudio jack sink, it is not stable.
Download tutorial and watch it in VLC. You need to install JACK plugin for VLC, it is not installed by default.

---

### Post by Koori Graywolf on 2013-04-22
Running "pulseaudio -k" before starting JACK and using VLC with JACK worked like a charm. Thanks for that and all your other advice, I really appreciate it. Sorry for the bother. Consider this thread solved!

---

### Post by chkneater on 2013-08-16
Yeah, well jack is still sucking.  Always something: doesn't remember the settings; tries to use the wrong card all the time; sets 'default' as something you don't want; routing all the connections is a headache; and it was supposed to be able to handle anything and keep it running for all your audio.  Hasn't happened and I've been using Ubuntu and other Linuxs' for years.  I wish Canonical would get off their a$$ and help these parttime developers.

Unrelated: there is a notebook with ubuntu pre-installed.  Everyone scream "yay"!! Jump for joy, EXCEPT get ready to start paying for Linux and Ubuntu, or certain 'apps' for Linux.  It's already happening.

---

### Post by Sylos on 2013-08-17
For card defaulting you can use alsa aliasing and similar tricks to pin the name of a card so the one you want is always selected. See here [http://alsa.opensrc.org/MultipleCards](http://alsa.opensrc.org/MultipleCards)

If settings are an issue then try starting Jackd with a custom command (pop it in a launcher or script on your desktop) then once its running start Qjackctl which will just jump on to the running server as the front end.

Cheers

---

