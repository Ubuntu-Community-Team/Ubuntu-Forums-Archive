---
title: "Sibelius sound problems"
date: 2009-06-14
forum: Wine
---

### Post by beak02 on 2009-06-14
Hi,

I've been trying to get music notation software to work on ubuntu and after several posts in the 'Multimedia' forums I have concluded that you can't get better than sibelius.

I installed my copy of Sibelius 5 under wine and it installed fine, ran fine but would not playback the music that I had in-puted.  I checked the playback devices and have nothing resembling 'Speakers' - just one entry labeled 'Midi Through'.

I tried this with a friends version of Sibelius 4 and got exactly the same problem.

Is this a WINE issue?  Is it just me?  I've heard some people have got it running under wine and Sibelius 4 has a 'Gold' rating at WineHQ.

Any help is much appreciated.

---

### Post by Amilo1718 on 2009-06-14
why don't you use Rosegarden?
wine will always be a setback (imho)

---

### Post by beak02 on 2009-06-14
I've had a play with rosegarden but it's not what I'm looking for.  I need to be able to print the scores as well as simply notate and play back.  I also need to be able to add dynamics, chords and other expressions above and below the music like I can with Sibelius.

---

### Post by beak02 on 2009-06-15
Anyone?

---

### Post by normthesamurai on 2009-06-28
Sorry I don't have a solution but I do have exactly the same problem, only with Guitar pro.  I'm assuming its a problem with wine rather then Sibelius

---

### Post by normthesamurai on 2009-06-28
Just found the solution to the midi problem:
[http://ubuntuforums.org/showthread.php?t=765889&highlight=midi+guitar+pro](http://ubuntuforums.org/showthread.php?t=765889&highlight=midi+guitar+pro)

You need to install tiMIDIty:
```

sudo apt-get install timidity

```

---

