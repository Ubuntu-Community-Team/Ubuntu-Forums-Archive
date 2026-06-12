---
title: "Need Audio Recording Tips!"
date: 2011-05-11
forum: Ubuntu Studio
---

### Post by iheartubuntu on 2011-05-11
Hi recording experts out there. Ive got a piano I recorded a long time ago and notice it sounds flat. How do I add more dimension to the sound? Looking for any tips or tricks out there really. Also, Id like to separate the bass and the treble with Audacity or another program and put them on different tracks. Is it even possible? Im not that much of a pro audio guy to figure this out. Totally appreciate any good advice. Thanks!

---

### Post by sgx on 2011-05-11
Hi, I like too add chorus fx for brightness, and very subtle delay fx to bring out depth, and use the various EQ fx to adapt the range of flat sounds, you can boost the lows and highs, and reduce the mid tones, etc to suit your needs.

The Rakarrack multifx app has all these, you can investigate the presets (some are electric guitar oriented, so beware volume levels vary) turn on and off the undesired ones, and save new ones useful to you.

I would make a couple of long loops of the key piano parts, that can play 15 minutes or so, while you experiment. You can cut out the loop, and cut/paste it to itself in audacity, and export as mp3 to save disk space. Rakarrack is a jackd program, so qjackctl is the gui for connections. Aqualung is an audio player that autoconnects to jackd, you can play the
loop, and change fx in rakarrack as you go, taking notes.
Rakarrack also autoconnects, so there will be only basic soundcard selection to set up in qjackctl, see its wiki page for links to screenshots/tutorials if its all new to you.

[http://en.wikipedia.org/wiki/Qjackctl](http://en.wikipedia.org/wiki/Qjackctl)


There are also many ladspa fx which, when installed, will be usable within audacity, select the desired audio portion in audacity, and choose the fx, adjust, and preview, or apply/undo as needed.

To separate a bass-heavy track, you can try rendering a mono track after using the 'bass boost', pan it hard-right, and export,
and do another mono track with less bass, more treble, panned hard-left,
re-import the bass-heavy track, and then export the whole, audacity should prompt you that it will mix a stereo track, hopefully the panning will remain untouched!
Cheers
(hours invested now, will pay dividends for years to come!)

---

### Post by cchhrriiss121212 on 2011-05-11
Sorry, but a bad recording will always sound bad, so the best way to get a good result is to re-record the part again. Sometimes you can get a bad part to sound acceptable, but it is not a good way to approach recording. 
There really is no shortcut or trick to getting a good sound, it always has to involve effort at the source (ie when you are recording) and not after. If you are not happy with the way something sounds before recording, you won't be when you come back to it later.

> Also, Id like to separate the bass and the treble with Audacity or  another program and put them on different tracks. Is it even possible?
Yep, just import the audio into 2 separate tracks, then use the equaliser on each one.

---

### Post by iheartubuntu on 2011-05-17
Chris121212 - thanks for the insight on recording. im stuck and there is no going back at the moment. i realize the best bet is to do it right the first time. time constraints have now limited me. if and when I can i will go back to the studio. TY!

SGX - thanks so much for taking the time to offer your personal experiences. i know what you mean spending hours :) i still could not get what i want so i asked here. I had never heard of Rakarrack before.. hope to add it into my arsenal of programs. thanks for the tips! much appreciated!

---

### Post by flemur13013 on 2011-05-17
Check these:

[http://www.hydrogenaudio.org/forums/](http://www.hydrogenaudio.org/forums/)

[http://www.audiomastersforum.net/amforum/index.php](http://www.audiomastersforum.net/amforum/index.php)

PS: Audition tastes great with wine.

---

