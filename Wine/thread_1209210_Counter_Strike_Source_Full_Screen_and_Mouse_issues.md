---
title: "Counter Strike: Source Full Screen and Mouse issues"
date: 2009-07-10
forum: Wine
---

### Post by brandonman on 2009-07-10
Hello! I just installed ubuntu on a new hard-drive I purchased from newegg. I was getting fed up with Vista's random crashes, poor performance, memory hogging, and random freezes. Anyways, on to the question!
 
I installed WINE, and decided I wanted to see if Steam and CS:S would work. I copied my Steam Folder over to the new hard-drive (It did not want to run off the old C drive. Not sure why). I got Steam to open, and launched Counter Strike Source. The screen was really messed up, with the text showing up strangely, and the background was distorted in an odd way. I went ahead and installed the Linux drivers from nVidia's website (That was a hassles... Problems with x Server running and everything else. God knows how I actually did it. :P) I then started up Counter Strike Source and everything looked fine. Then the weird issues started.
 
1: I have to move my mouse a LOT lower than a button on the menu to click it. (To click on Find Server for example, I need to move it down even below the "Create Server" button). Has anybody experienced this, or know how to fix it? The issue persisted even if I ran in windowed mode.
2: The game does not fill the whole screen. The task bar and the bar at the top (Sorry, forgot the name) still show up, while CS:S fills the area where the desktop or other applications would be. Is this how it should be? If so, is there a way to change it? (It is set to run in full-screen mode)
 
If I was unclear on anything, please let me know and I will try and answer as best I can. I'm new to Ubuntu and Linux Distributions, but I should be able to figure out whatever you throw at me. That's what happens when you grow up with too much time on the internet. ;) Thanks for taking the time to actually read this whole post! Once I get this issue fixed, I may just be running Ubuntu all the time! (Vista has caused me nothing but problems lately. And of course things run just fine after the issues. Like yesterday, it just froze up, and then on a reboot worked just fine. This cost me my first ever competitive match of CS:S. Four rounds in, and I crash. Thank God I noticed something was up and told my backup to come in on Ventrillo... If I could pin down and fix the issues, it would be one thing, but when you can't? Sheesh, it doesn't even crash for a reason.)

---

### Post by Duckter on 2009-07-10
I've had something similar happen, definitely down to drivers (and using dual monitors didn't help me). Can't offer a specific solution as I have an ATI card but I wouldn't worry too much about it as I think it's a fairly common issue thats easy enough sorted.

You will need some patience to get it running properly. I'm in a similar boat but further down the river. Just can't get CS running reliably. It will run for up to 30 mins then completely lock up the system and require a reboot. Any solutions I haven't tried are appreciated in here. I've exhausted every avenue I can think of or search.

---

### Post by brandonman on 2009-07-10
Hm... Since it appears it is a common issue, does anybody have any links to threads pertaining to this? Or if you can't find that, what would be a good search term for the forums? I have no clue what I should search for to turn this up. WINE "FullScreen not fullscreen" and Mouse position off Counter Strike? I'd probably only turn up my thread though. Any more help is greatly appreciated!

---

### Post by brandonman on 2009-07-10
That's weird. I went ahead and tried running it again today, and it works fine. The mouse position on the menu was correct, it went full screen properly, and I could play. Couple issues though:
1: It felt pretty laggy client side (Not a network issue)
2: It crashed after about 30 seconds to a minute of play. 

Ok, so the questions are coming!

Number 1: I installed Ubuntu 32 bit. I didn't think to install 64 bit. I forgot about that, and I need it to utilize all of my RAM. Is there any way to be able to just 'Upgrade' to a 64 bit, and have all the settings and everything in place (Of course I would need to redownload the video drivers) or will I need to do some other stuff such as just burn a new ISO CD and reinstall? 
2:How can I fix this crash after a minute of play? I'm not sure what kind of errors, if any, it spat out in WINE, because I had to ctrl-alt-backspace and restart the GUI, so the terminal I was running steam with is gone. :(

---

### Post by brandonman on 2009-07-11
Well... I went into WINE Configuration and changed the sound to OSS. The game does not crash now, but I have no sound. >.> It seems somewhere, I need to get the correct sound settings so sound works, but it doesn't crash. Any ideas?

---

### Post by Th3_uN1Qu3 on 2009-07-11
Time for some answers i guess.

You cannot upgrade to 64-bit, you will have to reinstall.

The sound issues can be fixed by removing PulseAudio as it does not play nice with Wine (actually it doesn't play nice with anything):

```
sudo apt-get remove pulseaudio
sudo apt-get remove alsa
sudo apt-get install alsa
```

Then go into Sound Preferences and set everything to ALSA, also set Wine sound to ALSA. That should work.

---

### Post by Duckter on 2009-07-14
Right this is a bit anal but ive installed ubuntu server 8.10 then installed xorg, alsa and wine (several versions - latest, 1.0 and a couple random ones)... and ive also gone as far as changing sound cards! I cannot get this damn thing to play more than 15 minutes without needing to kick it in the reset button!

Another point I'd like to add is when I do the stress test i get 120fps... but in game its 20-40 using dxlevel 70. Suggestions anyone how i get this stupid game working adequately? It's more a matter of principal now, honestly i can live without CS:S

I must have tried about every possible suggestion in all the forums now. Really cant think of anything else.

---

### Post by diggedy on 2009-07-14
I play CSS in full screen mode but with wine in a window (configure wine > graphics > emulate virtual desktop), I create the window so its about the same size as my desktop. I also runs caseys config2 (google this) and I tend to run at around 100 fps.

It crashes occasionally which could be down to the pulse audio, ive yet to try removing it. One thing you will need to do is disable the in game steam friends chat (from the steam settings menu) as this **always** causes crashes.

---

### Post by brandonman on 2009-07-15
Duckter's fix did it! Thanks a lot!

---

