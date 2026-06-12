---
title: "Terratec Phase88, JACK, Linuxsampler, et al"
date: 2009-01-31
forum: Ubuntu Studio
---

### Post by Unitas on 2009-01-31
I'm having some problems with several things. My goal is to run my Terratec Phase88 with Linuxsampler and Rosegarden. The phase88 has 8in/out with midi in/out and SPDIF in/out.

First things first, I'm running 8.10 with the linux-rt kernel. Running with the usual kernel doesn't seem to make a difference except for the kernel error message in Rosegarden.

Alsamixer detects the Terratec card, and I have made sure that all of the meters are unmuted. I have disabled the on-board audio in the bios. 

If I select "Terratec Phase88 ICE1712 consumer (ALSA)" or the "Terratec Phase88 ICE1712 consumer (DS) (ALSA)" in the system>preferences>sound window, I can hit test and the slider moves, no errors, but there is no sound output. There are errors if I select the multi drivers. If I click "Test" while JACK is running the sound menu crashes.

Rhythmbox crashes if I attempt to play anything.

in the Envy24 control panel I have set H/W 1+2 in Patchbay/Router to go to Digital Mixer L+R respectively. If I put audio into inputs 1+2 I can hear output and the meters in Envy move.

In the JACK control panel, I have everything connected, nothing is left out. If I select anything but default for the input/output device or inputs or outputs, JACK refuses to connect. If I leave them at default, JACK will run.

I start up linuxsampler server, for audio output drivers it says "ALSA,ARTS,JACK" but for MIDI input driver it lists only "ALSA". If I startup Jsampler and attempt to select an audio output device, I get an error that the JACK server isn't running when it is.

If I try to stop JACK, in the message window is just says "Jack is stopping..." over and over, but never actually stops. If I make it force quit and restart it, it will not connect, saying 'default' server already active. "sudo killall qjackctl" or "sudo killall jackd" doesn't do anything.

I really need help on this, Gigasampler/Sonar/Soundforge are the only things left that are keeping me attached to windows, and that setup worked terribly.

If you need any error logs or config files or more info just tell me where to find them or how to get them.

EDIT: The bongo riff at login plays. No sound after that though.

---

### Post by Unitas on 2009-01-31
Update:

I got Jack, Linuxsampler, and Rosegarden all playing nicely on my card.

However that is all that plays through the card. There is still no system sound. The bongo riff at login plays but that's about it.

---

### Post by Unitas on 2009-02-01
Another update:

I got the system sound to work out of the card, I uninstalled the Pulseaudio drivers and shutdown JACK. I don't know if the Pulseaudio drivers had anything to do with it, and in my noobness I never thought that JACK could be withholding the alsa drivers from the system sound. (Even though they are connected in the JACK connections?) This might be why while JACK is running alsamixer is unable to find any hardware from the terminal (No elems found). The gui alsamixer finds it fine. Who knows.

The only other issues I'm dealing with now is sometimes after startup the card disappears from ubuntu altogether. Rebooting brings it back. Another issue is loading certain samples crashes the server. At first I thought it was because my account didn't have the proper memory permissions. After changing that it still won't load, yet larger samples load fine. The suspect sample loaded fine in Gigastudio... /boggle

If this setup can remain stable, then I have no reason to go back to windows, save for the odd samples that do not load that I will probably never really use anyway. From what I can tell this setup works much better and cleaner and puts much less stress on the system than Gigastudio/Sonar. I just hope it remains this way.

---

