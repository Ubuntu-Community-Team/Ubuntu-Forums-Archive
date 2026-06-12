---
title: "PulseAudio RT network"
date: 2009-07-08
forum: Ubuntu Studio
---

### Post by norhild on 2009-07-08
Hi!

I'm interested in building a simple network (maybe 4 PCs) in which I need to be able to play sounds from one of the PCs into each one of the others.

I've thought about using PulseAudio and its great posibilities, but I'm a bit lost. 

I think it's all in config files at PA, but I'm not sure if this would work in real-time, I think so, since PA uses RTP, but I haven't succeeded yet.

Any ideas?

---

### Post by igorzwx on 2009-07-08
Do you have a poweful box?

One Fedora geek told me this:
"By the way, I don't think it is a 'bug' in pulse, it is the fact that
pulse is a sound server and runs at a specific frame rate.  It has to
move all sound streams to that frame rate in order to play through the
sound device.  It uses on the fly rate conversion, and this introduces
artifacts into the sound.  Again, I don't think you know what you are
doing here, and are drawing faulty conclusions from limited data."

---

### Post by norhild on 2009-07-08
Well, on one side I have centrino2 laptop (an Acer Aspire 5930G), which I wanted to make the main server (if I made it work, then I'd move in a proper one). 

On the other side, I have the 'client', a P4 ShuttleX, so... Yes, I'd consider it powerful enough, since both would be exclusively for that app (well, actually the laptop will be running a java app I've programmed).

Thx for the quick answer, anyway.

---

### Post by igorzwx on 2009-07-08
I am not a specialist.
But you may need a dual-core or quadro-core.
And the box might be much better than laptop.
Electric shielding is a problem.
Pulse is actually a creat thing, but...

---

### Post by norhild on 2009-07-08
> **igorzwx said:**
> I am not a specialist.
But you may need a dual-core or quadro-core.
And the box might be much better than laptop.
Electric shielding is a problem.
Pulse is actually a creat thing, but...
Are you sure of that?
May I have electric shielding problems for using PulseAudio?

I've never give it more than a quick thought, but... Sound in PulseAudio is sent over the LAN as any other data, isn't it?
In that case, I don't think that would cause any physical trouble (despite maybe little noises).

Besides, my laptop is already a dual-core (centrino 2 is the name for last year mobile C2D processors). And about the box,if it's just the client, I don't think I might need so much power...

I just want to find a guide or some quick steps to configure the PulseAudio thing, then if the performance is not good enough and I need a PC upgrade, then it'd be :)

Thanks anyway!

---

### Post by igorzwx on 2009-07-08
Yes I am sure.
Dell is more affected than IBM ThinkPad.

The howto you need was some days (2 or 3 days perhaps) ago on this forum.
I will search for it.

GOOGLE: "Ubuntu PulseAudio"

Ask markbuntu

---

### Post by Seq on 2009-07-08
If you have two PCs and the GUI controls for Pulse installed, why not just try it there? See if it works for you, then worry about configuring it manually if that is what you're after.

I've streamed sound between boxes in the apst, but I can't recall if there was any latency. I currently stream to an apple airport express which introduces a 7-second delay in playback. However that delay is due to the airport device's internal buffer, not pulse itself.

(note: I'm using an updated version of pulse)

---

### Post by igorzwx on 2009-07-08
Just open Synaptic
type pulse
and install all the staff you need

[http://www.google.com/search?q=markbuntu%20pulseaudio&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=markbuntu%20pulseaudio&ie=UTF-8&oe=UTF-8)

---

