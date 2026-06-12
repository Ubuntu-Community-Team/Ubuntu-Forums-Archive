---
title: "[SOLVED] Pulse Audio through Jack"
date: 2008-08-09
forum: Ubuntu Studio
---

### Post by markbuntu on 2008-08-09
This has finally been figured out and the solution can be found here near the bottom of the OP:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

You can now run any pulse/alsa/oss application and connect it to any jack audio application in the jack connection bay. It takes about 5 minutes to completely set up and has been tested by me in both Hardy i386 and amd64 and Ubuntu Studio 8.04.1 i386 and amd64.

I thought that since so many people in this forum use jack and Ubuntu Studio, it would be a good place to put a link.

:guitar:

---

### Post by Royke on 2009-06-07
Thanks markbuntu,

This was excactly what i've been searching for. The situation with me is that i would love to here skype-sound while i'm working on music, well maybe even record my friends voices for editing(with kind permission).
Now i'm gonna solve this (i hope) ):P

---

### Post by JOshea on 2009-09-14
I know this thread came out awhile ago but for AMD64 users with jaunty

one very important thing that is not covered here is using 
audacity to record whats coming through the speakers ie 
how to record songs playing on the web or wherever if you are using amd64 
jaunty - including flash files that are encoded ...

I switched everything to pulse audio from preferences on the main menu 
the "sound" selection on the main menu - sound preferences - except the main mixer - leave as is ...then 

use the pulse audio device chooser - go under the volume control 
and fire up audacity ...go under preferences there and choose pulse for audacity under both playback and record 

under the device chooser/ volume control -  go to recording tab - 
and hit record on audacity ...my card does not have a mix setting - but you can move the stream to the simultaneous from both playback and record tabs setting - and then you will see Audacity recording whats playing 

this took me way too long to figure out and you don't have to do any fancy work arounds or scripts to get it to work - I followed the link for jaunty but did not get rid of flash by adding the extra 32bit plugs to replace them but the others don't hurt to have - jack audio is not necessary and you can still save and load the wav files into something like Ardour 

cheers

---

