---
title: "Noob.  Help me!  (sb live content)"
date: 2010-03-18
forum: Ubuntu Studio
---

### Post by kenrothman on 2010-03-18
So, I've recently repurposed my old Dell 8100 (p4 2.6) to try to use it to do some home recording.

I've installed the latest and greatest ubuntu studio 9.10 and it looks cool.

Now i'm trying to get the basics down and be able to record something into, say, ardour.

I have a first generation Sound Blaster (sb) Live! with the LiveDrive (first gen, again).

Been googling and poking around, trying to figure out how to get the sound from the front panel 1/4" input to get recorded in Ardour.  not working.

only thing i've been able to do so far is go into the alsa mixer and unmute the input.  when i do that, and i make some noise into it (like, strum a guitar)... the sound comes out through my speakers.  so ... something *is* working.  

just not sure how to configure it so that that input gets directed into ardour.

my limited experience with similar software/hardware is with garageband on my mac, which seems easier to deal with so far.

but if anyone can offer some advice, or point me at a doc or faq i may have missed... that'd be much appreciated.

---

### Post by trulan on 2010-03-18
The first thing you'll need to do is get Jack up and running.  In the menu under sound and video, open Jack Control (or qjackctl as it is often called).  For the SB Live I believe you'll need to work at a 48000 sampling rate for things to work properly.  Other than that, you should be able to work with standard Jack settings, there are lots of web pages with lots of input on this issue.  Here's a guide for setting up Jack:
[https://help.ubuntu.com/community/HowToJACKConfiguration](https://help.ubuntu.com/community/HowToJACKConfiguration)

Another thing you'll want to do is run Ubuntu Studio Controls
[https://help.ubuntu.com/community/UbuntuStudioControls](https://help.ubuntu.com/community/UbuntuStudioControls)
and enable memlock.  This will eliminate one source of errors when trying to get Jack running.

There are a bunch of good links and guides here:
[http://wiki.linuxmusicians.com/doku.php?id=manuals_tutorials_and_howto_s](http://wiki.linuxmusicians.com/doku.php?id=manuals_tutorials_and_howto_s)

---

