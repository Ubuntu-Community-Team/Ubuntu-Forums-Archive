---
title: "No sound output in Ardour"
date: 2008-11-18
forum: Ubuntu Studio
---

### Post by its_jon on 2008-11-18
Hi.....

Im used to using audio tools in windows... just set up my envy24 chipset card to work in Ubuntu by switching to ALSA..... I don't know if this makes a difference but I want to use Ardour and I have no output from it.

I can't find a option in Ardour to check that its using Alsa... Possibly its a format issue as I imported a stereo Wav file into a stereo channel which it wanted to convert to 48 from 44....

Anyway.... I have sound through Alsa but no output from Ardour

any ideas ?.... something simple I guess.

thanks
John 
Scotland

---

### Post by cek on 2008-11-18
Have you checked the jack settings for where the ardour output is routed?  If you look in "Patchbay" in qjackctl, you should see Ardour's master outs routed to system_playback_1 and system_playback_2 (or something along those lines).

---

### Post by Stochastic on 2008-11-18
I would bet you need to look at the Ardour mixer and route the Main Output channel to your soundcard outs.

In Ardour press Alt+M (to view the mixer) then at the bottom of the Main Output strip there should be a button labeled Output - click that, then add your soundcard outs to the appropriate channels in the dialog box that pops up.

There shouldn't be any issue with the format of your wav file as ardour will resample things for you (at a better quality rate than ProTools actually).

This issue could also stem from you not having JACK configured correctly.  In Ardour's open dialog, if you haven't already started the JACK audio server, there will be a tab that says audio setup - this is Ardour's own JACK startup script.  It should work fine by default, but you should probably read up on JACK and qJackCtl.  The UbuntuCommunityDocs are a good place for this info:
[https://help.ubuntu.com/community/UbuntuStudio/GettingStarted](https://help.ubuntu.com/community/UbuntuStudio/GettingStarted)
[https://help.ubuntu.com/community/HowToQjackCtlConnections](https://help.ubuntu.com/community/HowToQjackCtlConnections)
[https://help.ubuntu.com/community/UbuntuStudio](https://help.ubuntu.com/community/UbuntuStudio)

---

