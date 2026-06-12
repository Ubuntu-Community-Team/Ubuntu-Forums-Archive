---
title: "Firewire and USB at same time?"
date: 2009-12-02
forum: Ubuntu Studio
---

### Post by sheehanje on 2009-12-02
I am currently using Ubuntu Studio 9.10 with a Presonus FP10 with very good results.  I use Ardour and Jackd as a damn good DAW solution.  Right now my band records live with the drummer using an electric drum kit, the bass direct in, and the guitar fed through a podxt live.  The vocals obviously come in on a Microphone. 

So far, the one inconvenience has been the full electric drum kit comes in stereo to the FP10, so we can't boost the seperate drums/cymbals after the track is recorded.  There is also sometimes cross triggering issues which would be nice to remove after the fact.

So, we are looking at recording the drums MIDI.  This is fine for the drummer, but I am not one, and I handle the recording end of things for the band and would rather not fool with his electric kit when I am going over things late into the night.  So, I am looking at getting an M-Audio Axiom 49 keyboard controller to help things along, but I have a few questions regarding this.

First, how well does the Axiom work on Ubuntu Studio and do I use the M-Audio keyboard via USB, or should I connect it to my Firepod via the MIDI interface?  If I do this, can I also wire the drums in MIDI, or can I only connect one device at a time?

I ask because the FP10 is a firewire interface, so I was wondering can JACKD handle firewire and USB interfaces at the same time?  While I have decent experiences getting Ubuntu Studio to work with the FP10, I have little to no MIDI experience.

Anyone running a similar solution that would care to share some insight in getting firewire, usb, midi to all play nice together?

---

### Post by kayosiii on 2009-12-04
The axiom works just fine with Ubuntu studio, it should work out of the box with the usb connection (If not it is just a matter of forcing a few kernel modules to load at boot time). (I have the Axiom 61 and a firepod)

Jack will pick it up as an Alsa Midi device so to use it with programs that support jackmidi you will need to run a bridging program. the command ```
a2jmidid -e &
``` will do this for you.. you can run that automatically each time you start jack using Jack Control (qjackctl).
Go into settings and go to the "options" tab make sure "Execute script after Startup" is checkd and copy the a2jmidid line above into the text box.

you can also put ```
killall a2jmidid
``` in the "Execute script on Shutdown" slot.

---

