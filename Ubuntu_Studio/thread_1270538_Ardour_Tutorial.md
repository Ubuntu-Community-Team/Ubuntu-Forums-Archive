---
title: "Ardour Tutorial"
date: 2009-09-19
forum: Ubuntu Studio
---

### Post by carusoswi on 2009-09-19
Where might I find a primer on using this application?  Took me most of the day (on and off) just to be able to start the program (didn't know you had to manually start JackControl, then hit the 'play' button before trying to start Ardour).

I'm not complaining.  A day spent exploring a new (well, new to me) application is a good metal exercise.  But, now, if possible, I'd like to move through the application to see how it might work for me.

I've managed to load and play wave files that I recorded in XP using Wavelab, but I had to fiddle around forever trying to get the signal out to my speakers.  I have yet to find the way to tie my PCI sound card to the Ardour playback signal.  If I switch my speaker mini-plug to the output of the onboard soundcard, I get playback.  Haven't tried to record yet, but I know from extensive use of Steinberg's Wavelab in XP that I cannot get acceptable results through the onboard card (too much static from onboard electronics or something).

While the onboard card is playing back, I have no clue what I did (or did not) to get it to work.  

If you can help with some suggestions, that would be most appreciated.  Better still, if someone can point me to more in depth sources, that would be appreciated even more.

Thanks in advance.

Caruso

---

### Post by trulan on 2009-09-19
Here's a page with a bunch of links:
[http://linuxmusicians.com/viewtopic.php?f=19&t=106](http://linuxmusicians.com/viewtopic.php?f=19&t=106)

---

### Post by carusoswi on 2009-09-20
> **trulan said:**
> Here's a page with a bunch of links:
[http://linuxmusicians.com/viewtopic.php?f=19&t=106](http://linuxmusicians.com/viewtopic.php?f=19&t=106)

Thanks for the reply and the info.

Caruso

---

### Post by madeinfamous on 2009-09-20
allo carusoswi,

this is what help me start from the beginning some time ago ;)

[http://www.vimeo.com/2867399](http://www.vimeo.com/2867399)

there is 3 videos, and they are the best i found, enjoy

:guitar:

---

### Post by carusoswi on 2009-09-20
> **madeinfamous said:**
> allo carusoswi,

this is what help me start from the beginning some time ago ;)

[http://www.vimeo.com/2867399](http://www.vimeo.com/2867399)

there is 3 videos, and they are the best i found, enjoy

:guitar:

All very helpful, thanks.  I don't know if you or someone else can help me with this additional problem.  My systems sound setup involves two cards, one onboard (not good for recording) and an Audigy 2 LS in the PCI slot.  Ardour would not pick up signal for me unless I rebooted, went into my bios, and disabled the onboard sound.  

Once I did that, I could open up Ardour and record through the mic input, but I have been unable to record through the lie input (which is where I want to pick up my signal as I employ a Tapco 6306 mixer.  So, my mics go to the mixer, and I want to capture the line out of the mixer to the line in of my sound card.  The Audigy driver software allows me to make those settings in Windows, but I don't know how to do it with Jack.

Also, once I disable the onboard sound, I get no sound from the line out of the Audigy card (as in listening to the tutorial on the 'net.  

I'm hoping there is some setting I need to make using Jack and not some insidious tangle that is the result of non-compatibility of my card with Ubuntu or Jack.

Suggestions would be most apprecited.

Caruso

---

### Post by raboofje on 2009-09-20
> **carusoswi said:**
> My systems sound setup involves two cards, one onboard (not good for recording) and an Audigy 2 LS in the PCI slot.  Ardour would not pick up signal for me unless I rebooted, went into my bios, and disabled the onboard sound.

Probably Linux recognized both cards, and chose the onboard card as card #0, the 'default'. When you disabled the onboard card, the Audigy became the default.

> I could open up Ardour and record through the mic input, but I have been unable to record through the line input.  The Audigy driver software allows me to make those settings in Windows, but I don't know how to do it with Jack.

Perhaps you can switch between line and mic in alsamixer?

> Also, once I disable the onboard sound, I get no sound from the line out of the Audigy card (as in listening to the tutorial on the 'net).

Did you start jack before opening the online tutorial? In that case Jack would have taken exclusive control over the sound card.

---

### Post by carusoswi on 2009-09-20
> **raboofje said:**
> Probably Linux recognized both cards, and chose the onboard card as card #0, the 'default'. When you disabled the onboard card, the Audigy became the default.



Perhaps you can switch between line and mic in alsamixer?



Did you start jack before opening the online tutorial? In that case Jack would have taken exclusive control over the sound card.

Thanks for the reply.  If I leave the onboard sound card enabled, alsamixer defaults to it when opened.  There is another choice (sigmatel something or other, not my audigy).  If I disable the onboard card, then, only that sigmatel choice shows up.  My PCI Audigy card would show up as CA106.

This machine and Audio have always been a bit hit and miss as far as Linux goes.  I think Linux correctly defaults to the onboard sound, and I think I'm lacking a proper driver that would make the Audigy fully recognized and functional to Linux.

Installing Ubuntu Studio has sorted a few issue, however, since before that, I could not get Ardor to start, and Audacious would not play back through the Audigy card.

If I were more adept at finding and recognizing names of things in Linux, I could probably sort it out faster.  I may be in a situation where I just cannot use the Linux side of things for professional audio.

I do own Steinbergs Wavelab 6.0 with dongle and Sony's Vegas Pro both on the Windows side, and they are quite capable.  I would love to have the choice to work in Linux, however.

BTW, in fooling around with this today, Ador outright crashed on me twice.  The windows just folded away and down she went, gone, poof.

Don't know what that's about.

I have learned a few things, however, and I know that I can get Ardour to record through my mic input.  I'll keep after it.

. . . . took me nearly five years to get my printer sorted out, but I did get it sorted, and I did not have to go out and purchase a special printer in the process.

Thanks again for your suggestions.

Caruso

---

### Post by raboofje on 2009-09-20
> **carusoswi said:**
> in fooling around with this today, Ador outright crashed on me twice.  The windows just folded away and down she went, gone, poof.

Don't know what that's about.

It shouldn't do that ;). You might want to try and start ardour from the console, and see if it yields any useful error messages when it goes down.

---

