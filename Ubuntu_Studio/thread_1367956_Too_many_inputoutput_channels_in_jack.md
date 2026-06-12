---
title: "Too many input/output channels in jack"
date: 2009-12-30
forum: Ubuntu Studio
---

### Post by cchhrriiss121212 on 2009-12-30
I have been able to get jack running perfectly apart from the fact I have too many inputs and outputs in the connections window. 
I am using an m-audio delta 44 soundcard which has 4 in and 4 out. Jack will not run unless I have 12 inputs and 10 outputs. Is it possible to display only 1 input and 2 outputs?

---

### Post by JC Cheloven on 2009-12-30
Hi, I don't own a delta44, but I think that the alsa controller for your soundcard (probably envy24 based) serves as well for other soundcards with more I/O. 

So it is normal for jack to show some more I/Os that you actually have. It happens also for me with a hammerfall 9632. Perhaps you'll have to guess which channel belongs to which connection, but otherwise, little to worry about.

---

### Post by cchhrriiss121212 on 2009-12-31
Yeah, it wasn't a problem to begin with for me, but it started causing me problems the other day when doing a multi-track project in Ardour. Each new track I do connects to a new capture input (so track 4 is connected to input 4 automatically). When I got to track 5 jack would not allow me to disconnect from input 5, and i had to restart jack.
I thought there might be a quick fix for this, plus I'm still curious why it displays in/out ports that don't physically exist?

---

### Post by RaumTrug on 2010-01-01
same is for my m2496, it has only 6 input channels (2analogue, 2digital and 2 monitor mixer capture), but shows a number of 12 in jack, so 6 dummy channels that do nothing. it's sloppy driver programming practice imho!

I think you can "hide" them by using the patchbay for doing connections with qjackctl, then you can even rename them.

other than that, just ignore the channels! they "exist" for the driver, but who knows if it is programmed properly to ignore input data: as you said jack/ardour kind of crashed when you connected the dummy channels, and that'd be real bad, and needs to be fixed!

---

