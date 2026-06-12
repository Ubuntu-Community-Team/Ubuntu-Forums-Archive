---
title: "ardour gtk2 won't start"
date: 2009-09-19
forum: Ubuntu Studio
---

### Post by carusoswi on 2009-09-19
. . . it complains that it cannot open Jack.  This application was installed with my installation of Ubuntu-Studio 9.04.  I have checked and everything 'jack' related seems to be installed on my system.  What am I doing wrong?

Ardour looks like a great application that I am anxious to try.

Thanks in advance for any advice.

Caruso

---

### Post by PrivateSNAFU on 2009-09-19
I think you need to make sure jackcrtl is open and jack is running.

---

### Post by trulan on 2009-09-19
If you installed Ubuntu-Studio 9.04, and installed the audio metapackage, you have all the pieces you need to use Jack and Ardour.

I never had any luck starting Jack from Ardour - but then I never tried very hard.  As was said, start qjackctl (Jack Control in the menu) and get Jack up and running from there.  It is far easier, and lets you isolate any problems.  Once Jack is up and running, then start Ardour.  It will recognize it and you will be good to go.

There are plenty of how-to's on the settings to use in Jack Control.  Search around and see if you can find something specific to your setup.  If you can't get it working, just ask.

---

### Post by carusoswi on 2009-09-19
Well, I didn't realize that, after you start the Jack Control application, you then have to 'start' it by clicking the 'play' button in the session.  Did that, and I was able to open Ardour.  Now, what's next.  As a test, I imported a wav file.  Can't hear anything when I play it.  What else am I missing?
Caruso

Started Jack Control.  It's running.  Started Ardor, named the new file 'test', clicked open, message: cannot start Jack.  Possible reasons include incorrect parameters or that Jack is already running (?).  I'm confused.  Sure would like to give this ap a test drive.

Caruso

> **trulan said:**
> If you installed Ubuntu-Studio 9.04, and installed the audio metapackage, you have all the pieces you need to use Jack and Ardour.

I never had any luck starting Jack from Ardour - but then I never tried very hard.  As was said, start qjackctl (Jack Control in the menu) and get Jack up and running from there.  It is far easier, and lets you isolate any problems.  Once Jack is up and running, then start Ardour.  It will recognize it and you will be good to go.

There are plenty of how-to's on the settings to use in Jack Control.  Search around and see if you can find something specific to your setup.  If you can't get it working, just ask.

---

### Post by trulan on 2009-09-19
Open Jack Control, then click the start button.  No need to click the play button (That's Jack Transport, useful for starting several applications playing/recording at one time).  Just click 'start', and if the percent readout turns green and gives you a number (10%, .157%, whatever) then you can start Ardour and all will be well.

---

### Post by carusoswi on 2009-09-19
> **trulan said:**
> Open Jack Control, then click the start button.  No need to click the play button (That's Jack Transport, useful for starting several applications playing/recording at one time).  Just click 'start', and if the percent readout turns green and gives you a number (10%, .157%, whatever) then you can start Ardour and all will be well.

Thanks.  I probably was actually referring to the start button.  It looks like a play button to me.  I wish there were some place where I could find some documentation on all this stuff.  Ardour looks like a nice application, but I'm having trouble figuring out how to control the output path.  I have two sound cards in my system - on onboard, another in the PCI slot.  I would like everything to flow through that PCI card, but when I set things so that you would expect in/out to go through that card, nothing happens.  I can listen through the onboard card, however.

I know I'm doing something wrong, but really have no clue at this point (although I'm further along now than I was this morning).

Thanks for your help.

Caruso

---

### Post by trulan on 2009-09-19
You can select which soundcard Jack uses in Jack control/settings.  It's the 'Interface' button.  You should have hw:0 and hw:1, one hw for each soundcard.

I posted a link to some Ardour how-to's in your other thread.

---

