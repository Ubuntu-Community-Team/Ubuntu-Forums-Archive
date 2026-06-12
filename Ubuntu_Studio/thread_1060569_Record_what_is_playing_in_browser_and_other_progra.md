---
title: "Record what is playing in browser and other programs too, basically &quot;sound output&quot; re"
date: 2009-02-04
forum: Ubuntu Studio
---

### Post by loop444 on 2009-02-04
I want to record what is playing on my computer and hear it at the same time. For example i play a youtube song or random homepage stream or audio file, the speakers play that sound, i want to record it, and hear it. it might be possible if i get one of those cords male-male to the mic in and output, but this is not really what iwant, i want the digital solution.

Ive tried jack, but when jack is running, i cannot hear the music and sounds from the browser. Just running jack, there is system and system in connections of audio, im not sure otherwise what try to configure, it is many options. 

With sound recorder, ive tried my preferences but everyone is recording from microphone.

Ive tried some other programs too. And audacity doesnt have that icon either. 

help? :shock:

btw im sitting on ubuntu studio latest release and computer is hp artist edition from last year, couldnt find soundcard info on it, though it may be in some manual, if important? jeje

ive looked already through many threads with same question

also how do you connect audacity with jack? cant find it in the connect box

---

### Post by HammerOfDoubt on 2009-02-04
You need to fiddle with Audacity some more. I do this with it all the time. Try looking in the preferences or options for a sound input/ouput setting. I wish I could give you a better answer, but I'm away from my own PC. I will get back on this thread when I get home and tell you how I have it set up.

---

### Post by loop444 on 2009-02-04
> **HammerOfDoubt said:**
> You need to fiddle with Audacity some more. I do this with it all the time. Try looking in the preferences or options for a sound input/ouput setting. I wish I could give you a better answer, but I'm away from my own PC. I will get back on this thread when I get home and tell you how I have it set up.
okay thank you, even worse, i now discovered audacity wont play sound to me :( i try to change in its preferences between 

ALSA: HDA Intel Conexant Digital hw;0,1
ALSA: iec958
ALSA: spdif

this is in audacity preferences-> audio I/O -> playback, maybe there are more places in it?

recording can there be set to alsa or oss


in my system preferences sound, there are quite very many to choose from, many alsa, oss, pulseaudio, HDA intel oss and alsa 

there are so many options, would take very long time to try all possible options out :)

though an important notice is that the only ones that actually manage to play the test sound audible for me is most of them.

i have now changed all of the playback ones to pulse audio sound server and i changed audacity playback to oss/dev/dsp and it now plays sound

though the input is still to come, ill try to fiddle a bit around

though there appears to be a big problem, cant use audacity for playback with those setting same time as browser....sigh lol

while browser is running i can only choose alsa, and it doesnt play sound, audacity :(

and since im looking to use the browser live to record and listen in the music production this is a problem.

---

### Post by neu2buntu on 2009-02-05
this is a very good post here that may solve your problem... i would probably use pulseaudio and jack together. give this a real thorough read before you change sound settings [http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by skullmunky on 2009-02-06
Usually in Audacity the "Alsa:default" is the one to try first.  The biggest limitation of using OSS is that only one app can use the sound hardware at a time, which of course completely ruins it for the thing you're trying to do :) 

First try and get your sound playing ok in audacity through the Alsa sound system;  then, for recording, open the Mixer (from the desktop volume control applet, not part of Audacity), look for the recording settings, and see if you can enable a recording device called "Capture".

---

### Post by skullmunky on 2009-02-06
Ack double post, delete please.  sorry.

---

### Post by skullmunky on 2009-02-06
screenshot showing settings.  (in KDE).

---

### Post by earthtux on 2009-02-09
I set both input/output devices to alsa default in audacity
playback is working but record fails which means nothing is recorded.

but record from the mic works, it just cant record what is playing.........
anyone can help?
thx
I am using 8.10
audacity 1.3.6
at
system->preferences->sound->audio conference->sound capture
I only get sound from "test sound" option
other options give me no sound....

I cant record sound with gnome recorder either.. no sound

---

