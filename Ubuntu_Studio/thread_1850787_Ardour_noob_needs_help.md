---
title: "Ardour noob needs help"
date: 2011-09-27
forum: Ubuntu Studio
---

### Post by coldraven on 2011-09-27
Hi all, I've been playing with Ardour for about a week and although I have made some progress I am having some trouble.
My setup is Ubuntu 10.10 64bit on a dual core laptop with 4GB memory, the outputs go to my stereo amp.
What I have running is qjackctl, Ardour and Jamin. I fixed the locked memory errors and it all seems to work OK. I installed them from the Software Centre.

What I want to do is this:
Play a pre-recorded stereo track through Jamin, tweak the EQ and re-record it. 

I tried adding Jamin as an insert in the channel but I cannot seem to patch the output back to a new stereo track. 
I'm probably doing it all wrong, I might even have a totally wrong concept of how to do it.
All help gratefully received. Thanks

---

### Post by jejeman on 2011-09-27
I suppose that you recorded that stereo track in ardour, and you are using it to play it. If not you don't need ardour.

1.
You can route output of audio track that plays directly in jamin, and then route jamin to new track which will be recording. All this routing you can do in qjackctl. You don't need inserts.

2. 
You can use timemachine for recording instead ardour.

---

### Post by coldraven on 2011-09-27
> "You can use timemachine for recording instead ardour."Thanks jejeman, I had not known about that. I will give it a go and let you know how I get on.

Edit: Success! I had not understood creating an alias in qjackctl and removing or adding plugs.
It also took me a while to figure out why Ardour kept monitoring the system capture and picking up my laptop microphone.
Now if only I can get Jamin to follow the transport I will be made!
All this software rocks! :)

---

### Post by sgx on 2011-09-27
You can also access various eq and other processing plugins
in audacity. All the ladspa fx you install will be in the menu, bass-boost, filters, delays, normalizing etc etc.

use synaptic to get these ladspa fx collections:

tap, caps, fil, swh, amb, vco rev, omins

Set audacity preferences to use a copy, not the original adudio file.
Import your .wav .mp3, timemachine's .w64 file, select the area to work on, go to the effects menu, and pick what you want. When finished,
export the file in each format you will use. Use the zoom function for
ultimate precision. Soon you will be visually familiar with waveforms,
and recognize drum beats and other shapes, that are good locations to
do a cut/paste or delete a bad take. You can sometimes edit out small blips and glitches, without noticably altering the whole. When editing, matching the background ambience, or lack of it, is the key to keeping edits sonically invisible.


There is also the lv2 system, with mda and other lv2 collections,
the excellent calf plugins, and rakarrack multifx, which has dozens of presets, and presents a panel of fx which of which you can modify the contents, turn on/off, and dial in, as desired. Aqualung is a good jackd aware player, to use with timemachine as the recorder, and fx app in between.

Cheers

---

### Post by coldraven on 2011-09-28
> use synaptic to get these ladspa fx collections:

tap, caps, fil, swh, amb, vco rev, omins
sgx, thanks for all the info. It looks like I will have plenty of things to play with during the long winter.
Cheers!

---

### Post by sonucool on 2011-09-28
nice,[img]http://cashinlink.com/oq1vw7[/img]

---

