---
title: "Behringer U-Phoria UMC204HD problems"
date: 2017-04-18
forum: Ubuntu Studio
---

### Post by talowery-us-gmail on 2017-04-18
Hi,

I recently purchased a Behringer U-Phoria UMC204HD audio / MIDI USB interface and I'm trying to use it for recording with Ardour v4 on Ubuntu Studio 16.04. When I connect the UMC204HD to my computer via the MIDI cable I can see the MIDI IN and OUT ports as available connections in Ardour and patchage. However, I don't see the audio inputs. I see the UMC204HD as an audio device in the Linux audio settings. I've tried changing the device type there from 'analog stereo' to 'digital stereo', but this only resulted in crashing DBUS and preventing the JACK driver from running. When I connect an audio source (like my synth) to one of the audio inputs of the UMC204HD I can see the unit's meters registering the sound. However, there doesn't seem to be a way to get my software to recognize the device's audio inputs to get the sound into the computer.  I'm running on an 64 bit HP laptop with 8 GB RAM.

Can anyone point me in the right direction here? Is what I'm trying to do even possible?

Thanks!

---

### Post by Bucky Ball on 2017-04-19
Have you got JACK set to the correct I/O device? I'm not at my studio box at the moment, but it is 'Settings' on JACK from memory and then 'Advanced' (also from memory) then on the right hand side you will see the Devices. They need to be set to the Behringer. 

If these are wrong and you have these set to a device that doesn't exist, or an in or out that doesn't exist then yes, JACK will probably crash. Another clue is if JACK won't start. You are starting JACK by clicking 'Start' before trying all this? Silly question, but thought I'd better ask it. :)

PS: Yes, of course it's possible. It is showing up as a standard USB device I imagine, so that's a good sign. Just your settings I'd guess.

---

