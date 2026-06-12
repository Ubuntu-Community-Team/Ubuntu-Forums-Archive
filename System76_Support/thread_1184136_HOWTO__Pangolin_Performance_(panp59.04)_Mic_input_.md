---
title: "HOWTO:  Pangolin Performance (panp5/9.04) Mic input works w/ Skype &amp; Sound Recorder"
date: 2009-06-10
forum: System76 Support
---

### Post by Happy_Pangolin on 2009-06-10
HOWTO:  Pangolin Performance (panp5) / Juanty / Mic input working with Skype and Sound Recorder

FYI, Just got my new Pangolin Performance yesterday, and I managed to get the mic to work with Skype and Sound Recorder.  The audio quality is pretty good, all things considered.  It is definitely better than some of the forum posts I read regarding poor mic audio quality.

So, not sure if this is the preferred method, but it works for me on my new Pangolin Performance running Jaunty Ubuntu:

............
HOWTO:  Pangolin Performance / Juanty / Mic input working with Skype and Sound Recorder
............


.......
Step 1) System > Administration > Services

Enable Audio settings management (alsa-utils)

......
Step 2) Click Speaker Icon on upper right top bar and then click Volume Control button to get Volume Control Panel.

Select HDA Intel (Alsa mixer) from drop down menu.

Click Preferences and select Master, PCM, Capture, Headphone, Input Source and then close.

In Recording Tab, make sure Capture level is maximum and unmuted.

In Options Tab, select Front Mic

.......
Step 3) In System > Preferences > Sound

In Sound Preferences Devices Tab, Sound Capture set to 'ALSA - Advanced Linux Sound Architecture'

Default Mixer Tracks set to 'HDA Intel (Alsa mixer)

Then use 'Shift select' to select all listed devices, especially Front Mic and Front Mic Boost.

......
Step 4) Skype > Options > Sound Devices

*** Important *** 
Unselect checkbox "Allow Skype to automatically adjust my mixer levels"

Set Sound In: HDA Intel (hw:Intel:0)

Set Sound Out: pulse

Set Ringing: Default device (default)

Now press the 'Make a test call button' to test.

.......
Step 5) Applications > Sound & Video > Sound Recorder

Set Record from input: Capture


* * *

All done!  :-)  Enjoy audio input from the builtin 'front mic'!

:popcorn:

---

### Post by PGScooter on 2009-06-12
I have no complaints at all. The battery life doesn't even bother me a bit. I don't even have much experience with Ubunut, but I've got everything loaded and it runs great. Things I do: statistics with Stata and R; LaTeX (using Tex Live 2008), perl programs, music, skype, watch DVDs, etc. Everything works great! Doing all of the above at once still hasn't maxed out my RAM.

A feature I like a lot is the silent mode. There is a group of three buttons in the upper left of the keyboard. Pressing the button furthest to the right puts the laptop in silent mode. I thought that the pangolin was very quiet normally, but this button puts it into stealth mode!

---

### Post by doubletruncation on 2009-08-08
Thanks so much for your howto! I was just trying to get the front mic to work with skype on a pangolin performance laptop, and your howto worked perfectly.

---

### Post by HamletDRC on 2009-08-19
it still doesn't work for me on a brand new laptop. Why does the microphone not work when the laptop comes out of the box? Anyway, I set the Volume COntrol -> Recording tab -> Capture slider - the toggle button is turned off so that you cannot capture. I can toggle it, exit the screen, and return to the screen, and my setting did not save. It is resetting to being toggled off. Same happens in Sound Recorder -> Volume COntrol -> Recording Tab -> Capture slider. WHy won't my changes stick?

---

### Post by vgrisham on 2009-09-16
Thanks for this thread! It works like a charm!

The recorded sound was rather quiet, so I added the front mic and front mic boost switches to the others you cited in step 2. I then cranked up the front mic boost to about half power and that did the trick nicely. 

Thanks again.

---

### Post by japhyr on 2009-12-11
Ditto, very helpful post.

---

### Post by atorch on 2009-12-16
How does this translate to 9.10?  I have a Pangolin and my mic doesn't work with either skype or sound recorder.

---

### Post by thomasaaron on 2009-12-17
It doesn't translate very well to 9.10.

My Pangolin is out for review, so if anyone can post screenshots it would be much appreciated. If not, I'll try to get some up in the next few days.

---

