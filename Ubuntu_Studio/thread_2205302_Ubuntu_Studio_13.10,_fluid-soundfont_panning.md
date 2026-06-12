---
title: "Ubuntu Studio 13.10, fluid-soundfont panning"
date: 2014-02-13
forum: Ubuntu Studio
---

### Post by royleith on 2014-02-13
First, a reminder that Timidity does not work with jack in 13.10. It can be kickstarted into working with the following:

> sudo service timidity stop
timidity -Os -iAD
^C

You cannot rely on the MIDI connections to be automatically set up so check in Connections or Patchage that Timidity is connected to your application if you get no midi sounds. I find that any program using WinASIO needs to be playing before the WinASIO MIDI ports appear in Patchage.

I started a project in Rosegarden by importing a midi file that someone else created for me. I am using fluid-soundfonts rather than freepats because there are missing instruments in freepats. I have searched the internet and installed the missing pats, but I lose interest with having to do it all over again each time I upgrade.

I wanted to do some extensive MIDI event editing and moved the project across to Reaper running in Wine.

Trumpet and Trombone were panned to the extreme right and could not be panned to the centre for any length of time and could not be panned left at all.

I thought it might be a Wine, Reaper or Rosegarden artifact, but playing back the exported MIDI file in Kubuntu gave just the same result.

It is a problem with fluid-soundfont, itself. Some brass sounds and some organ sounds are panned hard right by default. There may be more. I checked /etc/timidity/fluidr3_gm.cfg and all of the instrument settings are for 0 panning, so this is not the problem.

In both Kubuntu and Ubuntu Studio and with any program using Timidity the problem still exists.

Changing back to Freepats resolves the problem, but then there are the missing pats. Even the sample tune, The Rosegarden, played in Rosegarden has one or two missing instruments. Also, the freepats are a little wimpy compared with fluid-soundfont.

I notice that in /usr/share/sounds/sf2/ there are both fluid-soundfonts and TimGM6mb.sf2, but there is no .cfg file for the latter. The author claims that many config files should work and so I might have a go at editing fluidr3_gm.cfg to point to this alternative.

---

### Post by royleith on 2014-02-14
Talking to myself again!

I set up the .cfg file for TimGM6mb.sf2 and even more sounds are panned hard right. 

Audacious has a handy feature of being able to use soundfonts directly or to drive Timidity. It turns out that Timidity is loading soundfonts incorrectly. Using either TimGM6mb.sf2 or fluidr3_gm.sf2 give properly panned instruments when using the FluidSynth back end in the Audacious, AMIDI-Plug preferences.

It seems that Timidity has developed a number of problems in this latest release of Ubuntu Studio.

Since not all music editing software supports a FluidSynth back end, I have reverted to freepats in Timidity with the missing pats replaced and the .cfg file updated with the pointers to the added pats. Rosegarden will support soundfonts, but only with a Creative SoundBlaster card with the soundfont facility. I think they disappeared some years ago.

I do not link to the locations of the extra pats because I cannot be sure they are free and open. You can find them, yourself, by browsing the internet. /etc/timidity/freepats.cfg needs to have the additional lines referencing the additional pats. Be warned, some of the default pats are wrongly numbered in this file. The revised pat.cfg file is attached.[ATTACH]250338[/ATTACH]

---

