---
title: "LMMS versus JACK and Rosegarden"
date: 2010-01-24
forum: Ubuntu Studio
---

### Post by sulligogs on 2010-01-24
Hi all,

I'm not a musician or composer, but I've had a crack at producing music from time to time on various Windows audio trackers/sequencers and the other day I fancied a bash on my main operating system Kubuntu.

I poked around the web and found references to Rosegarden, MusE, MilkyTracker and Schism Tracker.  After installing Rosegarden and MusE I found out that I had to have JACK installed and running as well.  Not only with JACK, but also QSynth for MIDI synthesis.

And even then after tinkering around with these I still couldn't get any audio.  Apparently, I had to install a low resolution kernel, but even after doing so there was no change in circumstances.

So, in the eleventh hour, just as I was about to call it a day and forget about music production on Linux, I did one last search on Google for Rosegarden alternatives and came across this page:-

[http://alternativeto.net/desktop/rosegarden/](http://alternativeto.net/desktop/rosegarden/)

The first in the list at the time of writing is some software called LMMS (Linux Multimedia Studio).  I got it from the repositories with:-

```
sudo aptitude install lmms
```I fired it up and took a gasp at the gorgeous looking interface, very similar to Hydrogen (a drum kit based sequencer).  After taking a few minutes to get used to the interface I wanted to see what MIDI facilities it has.  I found that it could use Soundfont files which I previously installed with:-

```
sudo aptitude install fluid-soundfont-gs fluid-soundfont-gm
```The Soundfont files will be located in :-

```
/usr/share/sounds/sf2/
```In LMMS on the left hand side I saw a column of speaker icons.  To expand the Instruments Plugins panel I clicked on the top most icon.  In that panel was a section called Sf2 Player.  I hovered the cursor over that section and it automatically expanded.  Then I dragged that section across to the left hand pane of the Song Editor window and now I had a track for MIDI output.  Whoopee!

However, before getting it to work I had to point that track in the location of the Soundfonts files, which I mentioned earlier.  By clicking on its name of Default Preset I got a little window where I gave it the location of the Soundfont files and which patch/instrument to use.  Not only that, but in that window there were a ton of fancy options to play with, like chrous and refurb and envelopes and what not.

Overall, an excellent piece of software!

---

### Post by bigredtruck on 2010-12-18
Thanks for that, sulligogs. Saved me a lot of time.

---

