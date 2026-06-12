---
title: "Midi Input"
date: 2009-09-28
forum: Ubuntu Studio
---

### Post by euphonism on 2009-09-28
I'm trying to use Denemo for music notation, that is, use my midi keyboard in order to enter notes (like one would do in Sibelius for Windows). However, each time I select Midi Input from the Input menu I'm given an error message stating that it can't start Midi Input. I'm using a Delta 1010lt sound card and it's hooked up to a Technics SX-PR900. I have tried messing with qjackctl a bit but am confused that under the Midi tab no connections are being detected. Under the ALSA tab I have listed "14:Midi Through" and "20:M Audio Delta 1010LT" on both the readable/writable clients and "128:TiMidity" additionally under writable client. I've tried connecting these in various ways, starting jack, and then proceeding with Denemo to no avail. I don't really know where to go from here and any help is greatly appreciated.

Thanks-

euph

---

### Post by kayosiii on 2009-09-28
There are at the moment two different midi interfaces used by Audio programs on linux which are mostly incompatible but you can bridge them with a program. The midi tab in qjackctl represents jack midi which is quite new and only used by a few programs it has less features than alsa midi (the alsa tab) but is sample accurate. Jack midi was created to get around the fact that alsa midi can drift a bit.

Now as to your problem... Try hooking up a simple synth (Zynaddsubfx is what I usually use and try and get it working first). If that works we have to look at Denemo's settigs. If It fails we might take a look at your hardware.

---

### Post by euphonism on 2009-09-28
Ok I installed ZynAddSubFX. To get it to work I opened Jack Control, started it, then opened ZynAddSubFX. Once this was opened it appeared under the ALSA tab of Jack's connection window. Under readable clients I selected "20:M Audio Delta 1010LT" and under Writable Clients I selected "130:ZynAddSubFX" and hit connect. After doing this, the notes I play on my keyboard are now registering within ZynAdd. However, I tried repeating this process for Denemo with no such luck. Where to now? Thanks much for the help :)

-euph

---

### Post by kayosiii on 2009-09-29
Ok that means that your hardware works fine... this is good news...
Which means that the problem is with Denemo - since I have never used Denemo I am going to install it and take a look.

(update - I can't seem to get denomo to run for me at all - All I can find is this documentation in the manual
[http://www.denemo.org/doc/denemo-manual.html#id2678332](http://www.denemo.org/doc/denemo-manual.html#id2678332)). Have you tried MuseScore (mscore)? I have been able to get that to work

---

### Post by kayosiii on 2009-09-29
Ok I got denemo working... It appears to be using JackMidi as opposed to alsa midi (it shows up red rather than green in patchage).... Firewire based soundcards see the hardware midi ports as jackmidi but nearly everything else the hardware ports are alsa midi.

In order to use Denemo with your keyboard you are going to need to use a bridging program... There is one called a2jmidid and it is in apt-get...

It's a commandline program but you can have jack control launch it after you connect to jack automatically. To do this in "jack control" setup window go to options and tick the box that says "Execute script after Startup" type into the entry "a2jmidid -e &" (without the exclamation marks) This will start the bridge every time you start jack (the -e option is to bridge the hardware ports the & symbol tells it to run in the background)... It might be a good idea to close a2jmidid before closing jackd in which case tick the "Execute script on shutdown box" and type in "killall a2jmidid".

Hope that helps

---

### Post by euphonism on 2009-09-29
Followed steps as provided and Denemo is just freezing whenever I try to select an input type now :confused:

---

### Post by kayosiii on 2009-09-29
ok - I am using Karmic alpha6 -- so undo my last steps and verify in patchage that the midi inputs for denemo are red...

---

### Post by rshann on 2009-11-13
Ask in the denemo-devel mailing list/or on irc (freenode #denemo), things are moving very quickly in Denemo.

---

