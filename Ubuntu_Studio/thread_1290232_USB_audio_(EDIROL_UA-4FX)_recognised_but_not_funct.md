---
title: "USB audio (EDIROL UA-4FX) recognised but not functional"
date: 2009-10-13
forum: Ubuntu Studio
---

### Post by 2benglish on 2009-10-13
USB audio (EDIROL UA-4FX) recognised but not functional
On a clean install of ubuntustudio 9.04 on a Fujitsu CE70K7 my USB sound card is not functioning properly.

In System>Preferences>Sound it appears as an option with ALSA or OSS, but selection results in the following message:

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

Can anybody point me in the right direction?
What info do you need from me?

I have tried the sound card on ubuntu 9.04 and 8.10 on another machine with more success. On both I was able to use the card to capture and play in audacity only. JACK would not show the card in its connections window. Any pointers here would be appreciated, too.

Thanks.

---

### Post by 2benglish on 2009-10-14
I wouldn't mind getting this sound card working on any of the the ubuntu versions I have installed - 8.10, 9.04, 9.04 studio. Forget about advanced mode for now, I would be happy if jack would let me use this sound card so I can start using the nice looking packages available - Rosegarden, Hydrogen, Ardour.

At the moment I can capture audio and play audio through the sound card using Audacity.

When I go to the Sound options the only option on which the sound card works is with OSS. By selecting ALSA I get the message in the post above.

Using jack, with OSS as the selected driver causes jack to freeze.

Using jack with ALSA as the driver results in the sound card not appearing in jack.

How do I get jack to recognise this card? I have been trying for 4 days and nothing I have found has help me resolve this yet. It looks like there are plenty of people who have got this working. Please help!

---

### Post by sgx on 2009-10-14
In qjackctl, click setup, then at the far right, halllf way down,

click on the  >  icon for these:


input device  >
output device >

A list of detected audio devices will appear.

If its not there, run

sudo alsaconf

This will run the alsa sound configuration.

If alsa doesn't see it, unplug the unit if its usb, reboot, wait a bit after the system starts, connect the device, and check both the above again. Also, usb devices should be seen in the output of the commands

usbview
lsusb

If still nothing, there may be a modprobe command, or kernel module you
need to get, so google can be of great help, since edirol, ubuntu, modprobe, and kernel are very specialized keywords.

Cheers

---

### Post by 2benglish on 2009-12-07
A big mistake by me.
In jack I was expecting to see the name of the sound card appear as an input option in the audio tab. It was there all the time but labelled as System.

I hope this helps any others as unclued up as myself.

---

