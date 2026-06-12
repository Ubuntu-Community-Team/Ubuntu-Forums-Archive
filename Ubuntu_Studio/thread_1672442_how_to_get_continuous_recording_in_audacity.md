---
title: "how to get continuous recording in audacity"
date: 2011-01-20
forum: Ubuntu Studio
---

### Post by sevenenemy on 2011-01-20
title says it all, records and plays back fine just trying to get a track to record start to finish without having to hit stop and select the spot i want and then re-record when audacity decides to stop recording at specific parts of tracks.

---

### Post by sgx on 2011-01-20
Hi, sounds like a disk space issue, if you have 8 gig free disk space,
there should be no problem for a large recording.

Have you tried timemachine to record?
It opens a simple gui, and a connection in qjacktl, and connects to whatever you want. You can the import the file in audacity to edit and convert.

I start a new session when using audacity, for luck.

Cheers

---

### Post by sevenenemy on 2011-01-20
its not the hard drive i have 60gigs left, its when i get to lower frequency portions of songs that it stops playback, i have to press stop, select a few seconds back on the timeline and then record from there. it creates a new timeline "layer" its always the same spots on songs, when the db's and or frequency (not sure what you call the graphical sound wave display) get lower on the timeline. memory is solid 4 gigs plus a 4 gig swap in case i overload ram, so im stuck still thanks though

---

### Post by sgx on 2011-01-21
Have you tried using jackd as the recording device for audacity?
This may require installing libportaudio2. Audacity shows its
itself in qjackctl as portaudio, but only after pressing the record button,
so change prefs device settings to jackd, press record, press pause, then make connections in qjackctl.

Have you tried changing the bitrate and quality settings in audacity?

Does timemachine record OK?

[http://packages.debian.org/unstable/sound/timemachine](http://packages.debian.org/unstable/sound/timemachine)

Cheers

---

### Post by Pablo_F on 2011-01-21
Hi, 

Check Edit -> Preferences -> Recording.

Maybe you have "Sound Activated Recording" enabled? 

Cheers! Pablo

---

### Post by sevenenemy on 2011-01-21
the problem is that after i made the connections using patchage everything but pulse and default was removed from the device list, so there is no jackd, i tried a reinstall and nothing so then a complete removal reboot reinstall and still nothing, i am also still having problems converting audio files. i messed something up bad because it apears that i have no playback device at all, even though i still get playback if i set device to default, pulse does nothing and i know little about it other than i noticed it had network connection capability so i assume pulse is for using one machine's devices to record from another over a network.  

and unfortunately while i wish it was that easy pablo i dont have sound activated recording on, man i really wish it was that simple lol when i read your post i was like "oh chyea, thats gotta be it" heart was skippin beats while i opened audacity to check but nope, nuthin yet guys!

thanks so far keep the ideas comin if you got em please thanks!

---

### Post by sgx on 2011-01-21
Try timemachine, install with

sudo dpkg -i name-of.deb

get it here:

[http://packages.debian.org/unstable/sound/timemachine](http://packages.debian.org/unstable/sound/timemachine)

It has one big record button, and a volume meter, and it will
show itself in qjackctl. The default file format will look like

tm-2011-01-01T01:29:16.w64 

and can be loaded in audacity for editing,
and conversion, after you stop jackd/qjackctl.

timemachine -f wav 

will specify a standard .wav file to be recorded

Cheers

If time machine will not record when connected, reinstall. :)

---

### Post by sevenenemy on 2011-01-22
already have time machine installed as it is default with ubuntu studio audio packages but it will not open because of my patchage connection issues see the following i know you have seen it sgx lol

[http://ubuntuforums.org/showthread.php?t=1672395](http://ubuntuforums.org/showthread.php?t=1672395)

[http://ubuntuforums.org/showthread.php?t=1672417](http://ubuntuforums.org/showthread.php?t=1672417)

---

### Post by rg_stephens on 2011-01-23
Perhaps you could try an different version of Audacity. It might just be a bug in the program. You should be able to record until the disk fills up.

RS

---

### Post by sevenenemy on 2011-01-29
turns out its fixed after a wipe and fresh install of ultimate edition   thrillseekers unite. i linked the jack system captures to the system   playbacks and i suggest people refrain from doing this. :cool: solved

---

