---
title: "Going back home to ALSA?"
date: 2008-05-31
forum: Ubuntu Studio
---

### Post by DestriAero on 2008-05-31
Hey guys.

Earlier on everything was working - literally like 2 hours ago. Multiple audio streams, sound in flash the whole deal. Then I started getting crackling on recording and playback of flash files. So with no better Idea i went Hey lets try OSS, so i try to follow the installation instructions half way, and decide I want alsa after all.

I am running 8.04 ubuntu. So now alsa plays music, but no flash in firefox. Also in the gui sound options it says: "audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application." When i press test on ALSA.

Checked alsamixer, nothing is muted. Sound card is recognized.

SO i do have system sounds and music player audio, just no sound in firefox flash. Already have the aoss used as the DSP for firefox, still no help :(

Please help?

---

### Post by Stochastic on 2008-06-01
Can you post the link to the directions you were following to switch to oss, and describe at which point you stopped?  That might shed enough light on the situation.

---

### Post by DestriAero on 2008-06-01
Hey thanks for the reply:

Heres the post I was triyng to follow: [http://ubuntuforums.org/showpost.php?p=4874981&postcount=2](http://ubuntuforums.org/showpost.php?p=4874981&postcount=2) ;

Stopped at step 3. Configure linux-sound-base package (sudo apt-get install linux-sound-base if it is not already) ; 

I actually didn't blacklist ALSA due to the fact modprobe wouldnt let me access even with SUDO, so I configured linux-sound-base first to OSS. then I went back to ALSA with it. I have also reinstalled libesd-alsa0 ;

Thank you.

---

### Post by DestriAero on 2008-06-01
Fixed all problems by reinstalling OSS-COMPAT


Thank you very much for your attention, I have a few more questions bout other things like jack, but for those I will open a new thread. Thank you!

---

