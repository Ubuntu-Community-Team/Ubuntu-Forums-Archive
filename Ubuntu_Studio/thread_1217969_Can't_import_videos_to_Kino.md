---
title: "Can't import videos to Kino"
date: 2009-07-20
forum: Ubuntu Studio
---

### Post by iamnotloggedon on 2009-07-20
When I import videos from my camera, the videos are AVI but Kino shuts down if I import one of those, it seems to want only DV files. Is there another video editing software (that doesn't have hugely downgraded functionality) that accepts AVI or better yet, just a way to get Kino to import AVI?

---

### Post by squaregoldfish on 2009-07-20
Kino should certainly be able to import AVI files. It converts them to DV as part of the import process using mplayer/ffmpeg, so it might be worth checking that both of those are installed.

If it still doesn't work, run kino from the command line and see what errors are listed when it bombs. You can post them back here if you can't decipher them.

Steve.

---

### Post by iamnotloggedon on 2009-07-20
The terminal said nothing (I typed in "sudo open kino" and it worked though that was a complete guess). When I imported the video it asked if I wanted Kino to convert it or whatever it does and I said yes and it ran through as usual but once it finished the program closed. According to synaptic I have both mplayer and ffmpeg though there were tons of results for either search I had downloaded the most specific results.

---

### Post by squaregoldfish on 2009-07-21
Instead of 'sudo open kino', just type 'kino' in the terminal - that will ensure you get to see the messages that are logged.

Steve.

---

### Post by iamnotloggedon on 2009-07-21
Alright, well that solved a few problems as well as allowed me to get out of importing the AVI before it shut down Kino and here's what I got:

============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

Exiting...



The author? The videos came straight off my camera (HP M527 if it makes a difference).

---

### Post by squaregoldfish on 2009-07-21
OK, so it looks like you don't have a codec installed that will handle the movies from your camera.

It's most likely that you'll have to install the w32codecs package. You can get this from the medibuntu repositories - the instructions page ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)) will tell you how to set up your system to read the medibuntu stuff, and then the w32codecs package should turn up in synaptic.

Steve.

---

### Post by scotty2 on 2009-07-21
I started using Kino last night and had a similar problem - after recording about 3 seconds, Kino shut down.  I got it to work by selecting Frames for the time count.  May or may not be relevent to your problem.  

Video was analogue tape being played back through a camcorder which converted to digital.

---

### Post by iamnotloggedon on 2009-07-28
I have FFMpeg and Mplayer. Switching to frames as the time count didn't work though. As for the codec thing, getautomatix.com no longer exists. Really wish they'd post that in that forum seeing as it's one of the most used tutorials (I had no trouble finding that long before I decided to ask the forum). Fortunately I found automatix which downloaded the codecs for me. Still hasn't solved the problem. I'm going to see if the Synaptic has anything else on MPlayer and re-install Kino if so. I've tried everything I can think of; at this point I'm just guessing around.

---

### Post by Dubstar_04 on 2009-08-16
Please see this:

[http://ubuntuforums.org/showthread.php?p=7794905#post7794905](http://ubuntuforums.org/showthread.php?p=7794905#post7794905)

Let me know what you think.

---

