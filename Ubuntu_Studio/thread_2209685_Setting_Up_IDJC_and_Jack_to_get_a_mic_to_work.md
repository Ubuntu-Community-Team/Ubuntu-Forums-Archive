---
title: "Setting Up IDJC and Jack to get a mic to work"
date: 2014-03-06
forum: Ubuntu Studio
---

### Post by Chris_Marot on 2014-03-06
I'm totally new to IDJC, Ubuntu Studio and JACK. I am trying to set up IDJC so I can use a mic, but I cannot figure out how to make any sound come out of the DJ mic button. Ideally, I'd like to use my Blue USB mic, but I've even tried plugging in my headphones with a mic (just skullcandy) and seeing if that'd register in system_capture_1 and it doesn't. I'm really at a loss for how to set this up at a basic level, I guess. I've seen the posts about using interfaces on the setup screen in JACK and I['ve played around with it but to no avail. Any help - preferably step by step, would be MUCH appreciated. 

Thanks!

Chris
mondayswithmarot.com

---

### Post by jejeman on 2014-03-07
Plug in that USb mic, and give
```
arecord -l
```

---

### Post by brianmc on 2014-03-08
> **Chris_Marot said:**
> I'm totally new to IDJC, Ubuntu Studio and JACK. I am trying to set up IDJC so I can use a mic, but I cannot figure out how to make any sound come out of the DJ mic button. Ideally, I'd like to use my Blue USB mic

I'd go about this by starting **QJackCtl**, going into the *Setup* and changing the *Input Device*. You should be able to see your USB device as an available input. Once you've started JACK, run **IDJC** and pull up **Patchage** to check what's connected where. Make sure you've set the sample rate (in QJackCtl) to what the USB mic supports. The only USB sound device I've got is fixed at 44100kHz; it's also only 16bit resolution, meaning I have to check the "Force 16bit" option.

You can fire up a sound generator - say, Audacious ;), which you'd need to change to JACK output under *File* > *Preferences* - disconnect it from the system playback ports in Patchage, and try the various connections on IDJC to work out which is the input controlled by the DJ button (seems to be *ch_in_1*).

The previous poster suggests using the command **[FONT=fixedsys]arecord -l[/FONT]**, which will list the connected devices you can record from. By default JACK is probably using the onboard sound card for input and output; this would mean the only mic input which will work has to be wired to that card.

---

