---
title: "Rhythmbox with JACK in 10.04"
date: 2010-10-06
forum: Ubuntu Studio
---

### Post by zenon222 on 2010-10-06
In v9 I was able to use rhythmbox with JACK.  Since I loaded Ubuntu Studio 10.04 rhythmbox gives me the following error when I try to play a file

```
Couldn't start playback
Failed to link GStreamer pipeline: check your installation
```

TIA.

---

### Post by AutoStatic on 2010-10-06
Try running **gstreamer-properties** from a terminal (or with Alt+F2) and in the Default Output caption of the Audio part change Plugin to Custom and enter *jackaudiosink* in the Pipeline field.

---

### Post by zenon222 on 2010-10-06
Still doesn't work.  Other ideas?

---

### Post by Pablo_F on 2010-10-07
sudo apt-get install gstreamer0.10-plugins-bad

---

### Post by zenon222 on 2010-10-07
Was already installed.

---

### Post by AutoStatic on 2010-10-07
Weird. I'm now testing again and if you have the plugins-bad package installed it should even work without reconfiguring with gstreamer-properties :confused:

---

### Post by zenon222 on 2010-10-07
If I kill jackd then open rhythmbox, it doesn't complain and "appears" to function correctly.  Mind you I don't hear anything in my cans, but I think that's just because I have everything setup around the JACK server.

Now, check this out, if I do this:
- open rhythmbox
- "play" a file
- pause the playing file
- start-up jackd
- press play in rhytmbox

I get the error: ```
Couldn't start playback
Nothing to play
```

---

### Post by AutoStatic on 2010-10-08
AFAIK you cannot have a program that uses GStreamer as its backend to switch 'sinks' (so switch from Alsa or Pulse to JACK) while the program is running. You have to restart it. But I could be wrong, I'm not a GStreamer expert.

---

### Post by maghoxfr on 2010-10-08
I use pulse-jack to use pulseaudio through jack and it works.

---

### Post by Pablo_F on 2010-10-08
> If I kill jackd then open rhythmbox, it doesn't complain and "appears" to function correctly. Mind you I don't hear anything in my cans..
Have you checked pavucontrol? What audio card do you have?

I am with Auto. The normal way is launch first the audio server, then the clients. 

As a proof of concept, have you tried with exaile that also uses gstreamer? 

Cheers! Pablo

---

### Post by maghoxfr on 2010-10-08
Now that you mention I've installed it and tried it. It works too. I got the pulse-jack from falktalk's PPA. I wish I could post a proof of some kind but a picture won't just do because in the jack connections it just shows the "sink" it doesn't have a "Exaile" tab anywhere so you'll have to take my word on it!

---

### Post by Pablo_F on 2010-10-08
:) The question was addressed to the OP. but anyway. I am glad you discovered exaile. Nice, isn't it?

---

### Post by maghoxfr on 2010-10-08
Oh... :oops: LOL. Soooo, yeah...exaile it's nice, thanks.

---

### Post by zenon222 on 2010-10-11
My problem with exaile was the way it handled JACK sinks.  Every time a new track plays the sink disappears reinitializes itself in JACK and forcefully connects to "system".  The reason I run JACK is to filter all sound through jack-rack.

This meant after every song I manually had to disconnect and reconnect exail in the patchbay.

I just compiled 0.3.2.0, it has more options for audiosinks.  I tried copying my gstreamer-properties configuration to no avail.

Help?  Config screen attached.

---

### Post by Pablo_F on 2010-10-11
A good question for exaile developers. Or maybe a feature request.

By the way, you could try using qjackctl's patchbay, not the connections window. 

See instructions here:

[http://www.rncbc.org/drupal/node/76](http://www.rncbc.org/drupal/node/76) 

Cheers! Pablo

---

### Post by AutoStatic on 2010-10-12
Another option would be to use a player with solid JACK support, like Aqualung.

---

### Post by zenon222 on 2010-10-12
Thanks AutoStatic!  It annoyed me that aqualung always tried to forcefully connect with the "system" sink.  I dug around in the helpfile and discovered that if I start aqualung with this code:
```
aqualung --auto=jack_rack:in_1,jack_rack:in_2
```
It connects perfectly!

---

