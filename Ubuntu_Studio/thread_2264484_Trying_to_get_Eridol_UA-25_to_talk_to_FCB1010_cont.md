---
title: "Trying to get Eridol UA-25 to talk to FCB1010 controller for SooperLooper"
date: 2015-02-07
forum: Ubuntu Studio
---

### Post by kenslaptopshop on 2015-02-07
OK just putting it out there. Trying to get my Behringer FCB 1010 midi controller to communicate with my Edirol UA-25 USB Sound Card so that I can control Sooperlooper on Ubuntu Studio 14.04 LTS, really has been difficult to get it to work. I tried changing the hardware interface to the soundcard in qJackctl settings but that did nothing. Also installed MidiSnooper to see if I was getting anything but no dice. What would it take to make this work? TIA

---

### Post by kenslaptopshop on 2015-02-08
I have confirmed that the UA-25 can receive and transmit midi signals as it works in Ardour with my keyboard. So it seems that all my hardware is good and not the issue.

---

### Post by marseille2 on 2015-02-09
I have the Edirol UA-700 USB audio interface. Both have worked in Ubuntu for a long time, but sometime in the recent past ... a ''minor'' issue cropped up with the UA-700 (and from what I understand ... some other USB cards, too).

Long story short... I had to **disable on-board audio in the BIOS**. Sound is beautiful, and everything talks to each other perfectly. Dunno if this directly applies to your situation, but it's the starting point to troubleshoot our brand.

PS: Thanks to #ubuntustudio IRC for helping me figure it out. This is their tip. :guitar:

---

### Post by CrocoDuck on 2015-02-10
I have the very same midi foot controller and it always worked very good for me using [this]("http://www.m-audio.com/products/view/uno#.VNp_1HWsXZs"). As you said that the midi on the sound-card is working correctly under JACK I would suspect the issue being outside the computer. I remember I had some trouble making the controller send signals for real. If I am not wrong you have to navigate to any bank of presets first, and then you can operate the controller. Try to check the manual again.

---

