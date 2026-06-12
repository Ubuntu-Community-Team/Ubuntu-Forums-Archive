---
title: "PreSonus AudioBox USB and Jackd"
date: 2011-06-13
forum: Ubuntu Studio
---

### Post by jflesher on 2011-06-13
I can get my PreSonus AudioBox USB to work in Ubuntu Studio x64 11.04; the input and MIDI both work fine; but I'm having issues with Jackd, for one thing it locks up my web browser at times, cutting off pulse audio is normal, so getting video players or flash plug-ins to work is another issue; but the main problem I'm trying to solve is routing my Instrument input of the PreSonus AudioBox USB to jack so I can route it to apps so I can record it; I've had success routing the MIDI, but not the Audio; does anyone have this device working in jack or know how to solve this problem?

I have tried all combinations of setup in Jack, as far as input and output go; I have one built in sound card.

Update: Link to Troubleshooting info (ALSA Script output and command line output): [http://vetshelpcenter.com/media/misc/presonus/ts-presonus.txt](http://vetshelpcenter.com/media/misc/presonus/ts-presonus.txt) and hardware [http://vetshelpcenter.com/media/misc/presonus/lshw-list.html](http://vetshelpcenter.com/media/misc/presonus/lshw-list.html)

Thanks

---

### Post by Flaggmann on 2011-06-13
You might find some help in my replies to the posts below; they are all similar and
deal with how JACK, ALSA and Pulse interact. If pulse is just stopped, it will respawn and grab hardware; if it is just unistalled completely it can remove the entire graphical desktop leaving one in level 3 run mode.

"Disable pulseaudio elegantly" as outlined in one of the posts leave you with a clean ALSA JACK combination.
 
Posts/Replies:

[ubuntu_studio] No Sound with Biostar TF720 A2+
ERRRIMMAD
[ubuntu_studio] Maybe Useful Info for all sound problems posted
Flaggmann
[ubuntu] Upgrade to 11.04
uwe2006
[ubuntu_studio] ardour + aeolus
besser_dark

---

### Post by jflesher on 2011-06-13
> **Flaggmann said:**
> 
[ubuntu_studio] No Sound with Biostar TF720 A2+
ERRRIMMAD
[ubuntu_studio] Maybe Useful Info for all sound problems posted
Flaggmann
[ubuntu] Upgrade to 11.04
uwe2006
[ubuntu_studio] ardour + aeolus
besser_dark

Thanks for the ideas, but none helped; I don't know what I'm missing. 

I updated my post to show links to troubleshooting info.

---

### Post by kayosiii on 2011-06-22
I like the application patchage for audio routing.
[http://www.youtube.com/watch?v=3y4s6RRzkGY](http://www.youtube.com/watch?v=3y4s6RRzkGY)

Because It is usb you might also want to check alsamixer to make sure that the inputs are enabled and at a suitable level.

I am using a firewire presonus card which is a different situation but I find after starting jack that running pulseaudio --kill restarts pulse and flash et al all behave a lot nicer.

---

