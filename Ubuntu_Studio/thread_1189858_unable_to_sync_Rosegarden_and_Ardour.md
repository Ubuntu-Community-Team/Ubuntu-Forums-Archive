---
title: "unable to sync Rosegarden and Ardour"
date: 2009-06-17
forum: Ubuntu Studio
---

### Post by Capoeira on 2009-06-17
searched in the net but nothing helped.
trying to record some midi-tracks from rosegarden to ardour, but the syncing doesn´t work. with jacktransport rosegarden ends up a bit slower, begins syncronized but afer a minute or so u can hear it loosing the sync.

MTC, no way

how can i record my midi from rosegarden into ardour???

---

### Post by markbuntu on 2009-06-18
Are you using the rt kernel?
Is jack set up for rt?
You really need jack to run a maximum priority for everything to stay in sync.
Check in /etc/security/limits.conf and add or modify these lines

```

@audio - memlock unlimited
@audio - nice -10
@audio - rtprio 99

```

You can look through these. Maybe something is set up not quite right. 

[http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit](http://en.wikipedia.org/wiki/JACK_Audio_Connection_Kit)

[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)

[http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/](http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/)

[http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation](http://hubpages.com/hub/Recording-in-Linux-aka-Free-and-Open-Source-Digital-Audio-Workstation)

Excellent ardour tutorial here:

[http://out-of-order.nfshost.com/tutorials/ardour/](http://out-of-order.nfshost.com/tutorials/ardour/)

[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)

[http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/](http://www.ubustu.com/globe/2007/09/19/how-to-sync-hydrogen-with-ardour/)

[http://www.rosegardenmusic.com/](http://www.rosegardenmusic.com/)

---

### Post by kayosiii on 2009-06-18
How are you trying to sync the two...
Using Jack directly or something else?
Which program is Master?
Do the tempos match? 
does the recorded data in ardour match the tempo set (was it recorded against a metronome or a click track)?

---

### Post by Capoeira on 2009-06-18
> **markbuntu said:**
> Are you using the rt kernel?
Is jack set up for rt?
You really need jack to run a maximum priority for everything to stay in sync.
Check in /etc/security/limits.conf and add or modify these lines

```

@audio - memlock unlimited
@audio - nice -10
@audio - rtprio 99

```


yes, i am using realtime-kernel from 64studio 3.0 beta
jack running in rt
limits.conf is modified

> **kayosiii said:**
> How are you trying to sync the two...
Using Jack directly or something else?
Which program is Master?
Do the tempos match? 
does the recorded data in ardour match the tempo set (was it recorded against a metronome or a click track)?

in fact i allready gave it up, will play the midi-intruments directly in ardour, but if you have a solution.

i tried everything: jacktransport, jacktransport and MTC, MMC and MTC, rosegarden master and ardour slav and vice-versa. perhaps the problem is that the midi-tracks in rosegarden are allready recorded to audio tracks, rosegarden seams to have many problems with audio-tracks.
tempos both 110
recorded data in ardour match, testet it also with metronome now

---

### Post by kayosiii on 2009-06-19
if the tracks are already recorded to wave tracks why not import them into Ardour directly. I have only really tried syncing Rosegarden Midi to Ardour Audio.

---

### Post by Capoeira on 2009-06-27
so, the problem realy was that it was wave-files.
midi syncing works perfect wth jack-transport

---

