---
title: "Ardour3 alpha is searching for testers"
date: 2011-03-25
forum: Ubuntu Studio
---

### Post by zettberlin on 2011-03-25
Hello,

the day has come, the beast is out:

[http://ardour.org/a3_alpha1](http://ardour.org/a3_alpha1)

this first alpha-release is recommended for everyone who is willing to explore the new capabilities and opportunities that Ardour3 has to offer.

It s NOT recommended for day-to-day productive work since it will probably crash from time to time and such crashes can even destroy parts of your session.

But unlike the SVN-builds of the 3.0-trunk of 2010 and before, it runs stable enough to do real things in it. For me it sometimes runs for 1-2h whithout serious trouble while I compose stuff in the new MIDI-tracks and play around with the powerfull new automation-features and other wonders never to be seen before in a native Linux-Application for music-production.

The Ardour-Project asks kindly for your help testing A3. Your bug-reports are best put to [http://tracker.ardour.org/](http://tracker.ardour.org/) Comments, hints and wishlists are welcome on Ardours Mailinglistst.

And how shall we poor, non-tech-guru musicians install that monstrum, since it still is not, and should not be, build as a package for Ubuntu?

The Project offers A3 in a rolling-release-manner as ready to run binary distribution:

32bit:

[http://ardour.org/files/Ardour_x86-3.0alpha1_9185-dbg.tar.bz2](http://ardour.org/files/Ardour_x86-3.0alpha1_9185-dbg.tar.bz2)


64bit:

[http://ardour.org/files/Ardour_x86_64-3.0alpha1_9185-dbg.tar.bz2](http://ardour.org/files/Ardour_x86_64-3.0alpha1_9185-dbg.tar.bz2)

Just unpack the archive to any place you like and run its start-script. Say you have unpacked it to your HOME/Downloads/Ardour_x86-3.0alpha1_9185-dbg

then start it like this:

1.) start jack 

2.) open a terminal and type this commands:

```
cd
```

ENTER

```
Downloads/Ardour_x86-3.0alpha1_9185-dbg/bin/ardour3
```

The package runs on any recent Linux that provides Jack. I have it running very well under Ubuntu 10.4 and under Fedora14. Please provide enough disk-space: this application is about 800 MBytes big.

You may consider to install CALF (if possible its recent git-version) to get some LV2-synths. Ardour can drive external synths like Zynadd or Specimen also and external Hardware as well.


please help the good thing grow by testing it and reporting issues.

---

### Post by Pablo_F on 2011-03-26
Hi!

Thanks for the heads up. However, alpha3 is already announced. Better link to the ardour news and remove the direct downloads of alpha1, I think.

[http://ardour.org/node](http://ardour.org/node)

---

### Post by zettberlin on 2011-03-26
> **Pablo_F said:**
> Hi!

Thanks for the heads up. However, alpha3 is already announced. Better link to the ardour news and remove the direct downloads of alpha1, I think.

[http://ardour.org/node](http://ardour.org/node)

They are really gaining speed now - seems to be most recommendable to search for the latest directly under [http://ardour.org/node](http://ardour.org/node)

---

### Post by iandunham on 2011-03-26
Thanks for that. I'm downloading it as we speak.

MIDI with Ardour seems like it might mean no need for a program like Rosegarden or Muse?

---

### Post by zettberlin on 2011-03-28
> **iandunham said:**
> Thanks for that. I'm downloading it as we speak.

MIDI with Ardour seems like it might mean no need for a program like Rosegarden or Muse?

Muse, maybe, Rosegarden, not completely. Rosegarden has a good score-editor, Ardour has pianoroll only and a step-editor, that works with conventional Notation.

---

### Post by iandunham on 2011-03-28
> **zettberlin said:**
> Muse, maybe, Rosegarden, not completely. Rosegarden has a good score-editor, Ardour has pianoroll only and a step-editor, that works with conventional Notation.

Hmmm...I suppose you're right, I've never really considered score editing in Rosegarden good, though. That's one area in which Finale or Sibelius is just too far ahead to warrant switching platforms. I'm currently experimenting with the MIDI implementation in Ardour, and seems robust enough to deal with what most recording sessions require.

---

### Post by zettberlin on 2011-03-28
> **iandunham said:**
> Hmmm...I suppose you're right, I've never really considered score editing in Rosegarden good, though. 


OK in the sense: it existst and is usable I do not dare to judge, if it is state of the art.

> **iandunham said:**
> 
That's one area in which Finale or Sibelius is just too far ahead to warrant switching platforms.


Could you give 1-2 examples of features in these, that are missing in RG?

> **iandunham said:**
> 
 I'm currently experimenting with the MIDI implementation in Ardour, and seems robust enough to deal with what most recording sessions require.

Yeah -- works quite OK for me also. The most annoying bug that still existst is, that the last note in a region often got stuck if I clone a region. Especially if I loop 3-4 regions.
Do you have this trouble also?

---

