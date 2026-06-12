---
title: "Counter Strike 1.6 sound delay"
date: 2009-12-10
forum: Wine
---

### Post by farcyde21 on 2009-12-10
Currently Running:
Wine - 1.1.33
Ubuntu - 9.04
CS 1.6 Video - OpenGL
Wine Audio - ALSA or OSS (also previous had pulseaudio installed but I removed it)

When I load up counter strike every sound is delayed close to a second which greatly affects gameplay.  I havent noticed this in any other app but I dont run too much else through wine.  Can anyone help with this?

---

### Post by lightstream on 2009-12-13
I had this 'one sec delay' issue if I tried to use ALSA from Hardy Heron onwards (when pulseaudio was introduced).

But since Jaunty Jackelope, pulseaudio seems to work just fine with Steam, and everything else.

---

### Post by farcyde21 on 2009-12-14
I reinstalled pulseaudio and am still having the same problem. No change, hasn't gotten better or worse, by changing to OSS, JACK or any other sound option in wine.

---

### Post by The_swede66 on 2009-12-15
I have also the sound delay, but I´m not sure if it´s soundcard
or something else making this delay.

I have the Creative X-FI Extreme gamer card.

---

### Post by dragonatthegate on 2009-12-15
Been wrestling with the same sound delay problem with World of Warcraft, under Ubuntu 9.10, Wine 1.1.31.

I *think* I've fixed it.  

Try this:

Run regedit and at the following string:
HKCU/Software/Wine/Alsa Driver/UseDirectHW=y

And of course, make sure that your ALSA driver is the one selected in winecfg.

---

### Post by The_swede66 on 2009-12-15
Tnx, it worked:D

Now it´s only some graphic lagg.

---

### Post by Bwathke on 2009-12-15
I had sound delay on EVERYTHING I ran then I put on new speakers and it all worked out :/ (You can try updating WINE if it wont mess up other things you have on there)

---

### Post by farcyde21 on 2009-12-15
Do you mean :
HKEY_CURRENT_USER
-> Software
--> Wine
---> Alsa Driver

then 
Name: UseDirectHW
Type: REG_SZ
Data: y

???
I'm a relative newbie to linux so your shorthand kind of confused me.  If what I have above is right, I now have an issue where it is saying that registry item is already in use.

---

### Post by farcyde21 on 2009-12-15
I had to create the Alsa Driver folder and the value (as a string value). Now I also have NO sound whatsoever (not even outside of wine) and CS takes much longer to load (worth it if I can get the sound to work right)

---

### Post by lightstream on 2009-12-15
your lack of sound outside can't be directly caused the change in the Wine registry, as that only affects Wine programs. Linux itself doesn't use a registry, Wine only provides one for Windows programs.

The only thing I can think of is that maybe a Wine program is hogging the sound card so regular Linux apps can't use it.

---

### Post by farcyde21 on 2009-12-15
If I close pulseaudio, sound does comes back to non-wine apps so whatever that registry edit was it doesnt help me.

---

### Post by farcyde21 on 2009-12-15
Closing pulseaudio (from the System Manager) brings sound back to non-wine apps.  So whatever that registry edit is supposed to do, it seems to be overloading my sound card or muting sound all together.

---

### Post by vitorgatti on 2009-12-23
SOLUTION (worked for me):
Like **dragonatthegate** said, but more detailed:

- Make sure you are with **ALSA Sound Driver** checked in **winecfg**
- Open a Terminal and type: **wine regedit**
- Go to **HKEY_CURRENT_USER\Software\Wine**
- Create, if necessary, a new key called **Alsa Driver**
- Inside Alsa Driver, create a new **DWORD Value (REG_DWORD)** named **UseDirectHW** and with value **1**
- Close the registry editor and all other applications running with Wine (or simply restart your computer)

- Try to play CS 1.6 now. Sound should be working without delays.

Good luck!

---

### Post by kwesadilo on 2009-12-23
I have the same sound delay problem as farcyde21. I also get it when I'm running Half-life 2 in Wine. I didn't have this problem until I upgraded to Karmic from Jaunty. I tried the posted fix, but it doesn't seem to have done anything.

Edit: I'm running Wine version 1.1.31. I don't have any sound problems outside of Wine. Running the game with PulseAudio disabled via pasuspender didn't change anything.

---

### Post by dothem on 2011-02-05
No need to install the hardware acceleration, it is enough just to put in the settings "winecfg > Audio > ALSA (emulation driver). And in the game settings to register the console _snd_mixahead "0.012". If there is a wheezing sound, increase the value _snd_mihahead.

---

