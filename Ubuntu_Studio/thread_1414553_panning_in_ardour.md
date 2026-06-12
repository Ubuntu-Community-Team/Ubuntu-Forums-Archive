---
title: "panning in ardour"
date: 2010-02-23
forum: Ubuntu Studio
---

### Post by extendedping on 2010-02-23
Hi I am new to recording (working on my first song in ardour) and have a quick question. when you pan a track you pull the slider say to the right...isn't that supposed to make the track more prominent on that side? I am recording a mono guitar track and pulling the slider to the right. but the playback in my headphones (and through speakers once it is turned to a wav file) plays back on the left speaker. hmmm...

---

### Post by Stochastic on 2010-02-23
You may have something wired backwards (left connected to right) either in your software or hardware routing.  Check your entire audio chain.  Also, does this occur in other programs with panning ability on your machine?

---

### Post by extendedping on 2010-02-23
still looking for an app I can test panning in. my signal is guitar -- cable -- vox tone lab -- out left mono -- into firepod first port -- out to computer via firewire -- into ardour via first input (mono) and to master bus.

---

### Post by Stochastic on 2010-02-24
If you're modifying a mono signal with pan, then be sure that you troubleshoot the output chain, not the input chain.

Look at patchage or qjack-ctl's connections and your physical output connections.

Try modifying the panning in Ardour or Rezound - you may need to export your ardour recording to a wav file to do this, or re-record some mono guitar into the new app.

---

### Post by extendedping on 2010-02-24
ok not sure if I am doing this right. looking at pacthage I see the track (call it guitar right) that is panned right but playing on the left. it is under the "ardour" tab, it connects guitar right/out1 -- master/in1 and guitar right/out2 -- master/in2. then I have ardour master/out1 -- system playback1 and ardour master/out2 -- system playback2. again there is just a usb cable between my firepod and my computer. hmmm so it looks good to me I can't understand why its is flipped. is it possible there is actually a bug in ardour? my version is 2.8.2. I know mute (or was it solo) did not work and I had to google to find out some setting in the hidden ardour home dir files to change. hmmm. I don't know what else to look at. not the end of the world as if panning works it doesn't really matter if left is right etc. but it is a bit confusing to me.

---

### Post by extendedping on 2010-02-24
also if this is helpful, under the export session here is what I have checked...
master out-1 --- left
master out-2 ---      right

---

### Post by cchhrriiss121212 on 2010-02-24
In order to pan in ardour, all I see is a movable line that goes up or down when I click on pan. I think up pans right and down pans left.
What slider are you talking about in the first post?

Also do you have a link/instructions for that mute bug?

---

### Post by extendedping on 2010-02-24
the bug...(mute)
[http://ardour.org/node/2773](http://ardour.org/node/2773)

also on an unrelated note the foss manual for ardour told me dragging a region over another on the same track would create something called a crossfade, but all it did was mute one of the regions (the one dragged over) so I am thinking that ardour is a great app but a bit buggy.

---

### Post by robeast on 2010-02-24
I have practically the exact same setup (Mono Guitar >> Mic >> Firepod >> Ardour >> Master Out) and you must have your cables crossed from your master out to your monitors. Just swap them and enjoy.

---

### Post by extendedping on 2010-02-24
hmm my only cable to the pc is my firewire...then I have headphones in the headphone jack, they are labeled left and right. I also made sure my little crappy speakers are right and left (they say right and left) so I don't know how I could have a cable crossed. a physical cable that is.

---

### Post by extendedping on 2010-02-24
ok mystery solved and thanks all for replies. I have no idea how it happened. I will swear on anything it was not me but it somehow must have been. looking at the master bus there are 2 panners a top and a bottom. somehow the top was panned right and the bottom was panned left. I flipped them and now everything is good. I fired up an new session to see where they are by default and yup top is supposed to be left and bottom is supposed to be right. ok so I must have done this. I guess I'm a moron for a) doing that somehow and b) swearing I didn't have or have no memory of doing it. 

yea ardour is buggy. 

as buggy as the guy using it :(

---

