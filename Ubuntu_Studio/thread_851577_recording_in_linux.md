---
title: "recording in linux"
date: 2008-07-06
forum: Ubuntu Studio
---

### Post by AnLGP on 2008-07-06
i have a midi connector that connects microphone to midi and midi to computer.  I play through my guitar amp into audacity and can save it as a .mp3.

At least, on windows I could.  I can't find my windows install and want to know if this is possible to do in linux.  I'm using debian.  I have all the necessary things (disc, midi, microphone) but am unsure if I can download it to the HD and set it up.  Also I never did figure out JACK.

I have it hooked up and it seems to be recognizing the microphone.  I can play guitar and hear it in the headphones plugged into the midi connector but when I try and record audacity doesn't record it.

---

### Post by edm1 on 2008-07-06
Not exactly sure what your problem is. What type of midi interface do you have? Do you have drivers installed for it (if drivers exist for linux at all)? If your soundcard/interface will work with linux (can check at the [ALSA website]("http://www.alsa-project.org/main/index.php/Matrix:Main")) then yes you can record audio to audacity or even better ardour. I've never used midi but i'm confused at how you are sending analogue audio through it, i thought it was purely digital.

---

### Post by AnLGP on 2008-07-06
It's an "M-Audio Fast Track Guitar|Mic Recording Interface".  My sound is recognized (I can play music and hear videos, etc.  My mistake it's not midi :)

[http://www.m-audio.com/products/en_us/FastTrackUSB-main.html](http://www.m-audio.com/products/en_us/FastTrackUSB-main.html)

---

### Post by edm1 on 2008-07-06
after a quick search ([http://ardour.org/node/245](http://ardour.org/node/245) and [http://audacityteam.org/forum/viewtopic.php?f=16&t=5077&p=20067](http://audacityteam.org/forum/viewtopic.php?f=16&t=5077&p=20067)) it appears the card is kind of supported using a generic usb driver but it looks like people are having trouble with hissing sounds. Comes down to the old problem of hardware manufacturers not releasing linux drivers or specifications for their products.

---

### Post by AnLGP on 2008-07-06
But it should still record, right?

---

### Post by AnLGP on 2008-07-06
I've got audacity running and the preferences set for playback and recording to Alsa:Fast Track USB Audio (hw:1,0),

Can anyone tell me if I'm on the right track?  Please and thanks.

---

### Post by Ed J on 2008-07-16
I've been going through some issues with sound and I've had lots of luck looking in the Preferences... section of the software I'm using and ensuring the correct audio is setup.  ex.  In Hydrogen: File > Preferances...> Audio System (Tab) > Audio Driver.

  For Ardour I had play around with JACK a little to get the sound patched correctly. This was because I have an extra sound card that I wanted to use instead of the onboard one.

  I also installed the Gnome ALSA mixer, make sure the record check box is checked for the sound source so that it gets routed correctly when recording.  That burned me for hours.

GFL
Ed

---

