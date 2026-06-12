---
title: "Audacity and normalization of various files"
date: 2008-06-22
forum: Ubuntu Studio
---

### Post by DMurray on 2008-06-22
Hi, everybody.

I'm trying to switch from Cool Edit to Audacity, and haven't figured out how to do some basic tasks, for example:
I have 10 songs in mp3 format, different artists, different volumes, which I want to record to an audio CD. First I need to normalize everything so that 1 track doesn't play louder than other track.
That was easy to achieve using the Amplify option in CE, but the screen showed the output volume so I could know the amount of amplification to add or subtract from a track to make them equal.
How is it done in Audacity?
Thanks in advance.

---

### Post by horace on 2008-06-23
Just select the whole track and choose Normalize from the Effects menu - I have only used the default settings, but that has worked fine for me.

---

### Post by vanadium on 2008-06-23
Audacity indeed automatically suggests the gain needed to achieve 0 dB for the loudest sample.

However, I have a better suggestion for what you want to do. Normalizing does not account for differences in perceived loudness. Highly dynamic music will sound more quite than highly compressed popsongs from the last 20 years. To adjust the volume such that the song sound equally loud, you could use mp3gain first on (a copy of) your mp3 files. Afterwards, you can import the tracks in Audacity and apply normalization on the whole bunch of songs at one, keeping their relative loudness as determined by mp3gain.

---

### Post by DMurray on 2008-06-23
I tried the normalization via Effects menu, for 1 file at a time. To be honest, I didn't notice any change, I could be wrong of course.
As for mp3gain, never heard about it, but I understand the solution.
By batch-loading of the files, do you mean having a single instance of the program (audacity) and all the songs as tracks? When I try to load a second song, audacity will do it in another instance, that is, it would be impossible to batch-process the stuff.
Thanks a lot.

---

### Post by hookzilla on 2008-06-23
Though I'm not a pro at this, I use both Audacity and MP3Gain.   When I build a mix for a CD, I use MP3Gain mostly.  I copy the songs to a temporary directory and select them into MP3Gain to eaualize the volumes.  I  use Audacity more for individual songs, especially when converting LPs to MP3 files.

---

### Post by vanadium on 2008-06-23
> **DMurray said:**
> I tried the normalization via Effects menu, for 1 file at a time. To be honest, I didn't notice any change, I could be wrong of course.

Usually, songs you ripped from CDs are already at maximum scale.

> 
By batch-loading of the files, do you mean having a single instance of the program (audacity) and all the songs as tracks? When I try to load a second song, audacity will do it in another instance, that is, it would be impossible to batch-process the stuff.
Thanks a lot.
It is a matter of importing the different songs into one session.

I agree fully with the comments of hookzilla.

---

### Post by DMurray on 2008-06-24
I just downloaded mp3gain and found a very simple java interface for the basic work:
[http://www.step.polymtl.ca/~guardia/javamp3gain.php](http://www.step.polymtl.ca/~guardia/javamp3gain.php)

It looks like everything works. I'm listening to everything processed, then will do the final polish at Audacity, if needed.
Thanks for all the suggestions, everybody. In case something is still missing, this thread is already in my favorites. :-)

---

