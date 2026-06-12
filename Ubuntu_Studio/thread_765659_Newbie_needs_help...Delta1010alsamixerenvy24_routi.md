---
title: "Newbie needs help...Delta1010/alsamixer/envy24 routing"
date: 2008-04-24
forum: Ubuntu Studio
---

### Post by rayj on 2008-04-24
Hello, everyone. I'm trying to understand how audio gets routed around my system. Currently (temporarily), I'm using the same computer for my multitrack recordings and general internet surfing, multimedia playback, etc.

My question is this: I've managed to get everything to work just fine, but I don't completely understand the routing. For example, all my audio playback is being streamed through outputs 1 and 2 on the Delta 1010, and I see the meters registering the playback from within the envy24 GUI...however, any manipulations of the mixer controls there don't effect the sound from, say, flash media playback at all...

I'm using Ubuntu Studio 7.10. I have all the system preferences for sound set to the ALSA drivers, and the default mixer tracks are labeled as the MAudio Delta 1010. Under this heading, there are several outputs listed...IEC958 Multi, IEC958 Multi 1, H/W multi (null to 7), Multi (null to 7), etc. Is there any documentation that details what these terms mean? I understand a bit about it, but...well, obviously not enough, as I cannot, say, figure out how an audio stream from an online flash file is routed...

I'm trying to get a better understanding here of exactly how my audio is routed. Please excuse me if the information is readily available...I've been looking for awhile, to no avail. Thanks!

---

### Post by d_in_Conduct on 2008-05-04
IEC958 usually refers to a sound chip built in to the motherboard.  Try disabling that in the BIOS and see if flash & stuff gets routed to the Delta automatically.  There might be a Device setting the the Preferences of whatever software is playing flash or whatever else was not going through the Delta and with the on-board sound disabled, you should be able to select the outputs you want.

---

### Post by alexforcefive on 2008-05-04
Did you run asoundconf in the terminal? type "asoundconf list" to get a list of your soundcards, and then "asoundconf set-default-card (cardname)" to make that your default. Then I think the mixer should work

How are you finding the 1010 on linux? I've been having a terrible time with my soundcards, and I was thinking of buying a 2496.

---

