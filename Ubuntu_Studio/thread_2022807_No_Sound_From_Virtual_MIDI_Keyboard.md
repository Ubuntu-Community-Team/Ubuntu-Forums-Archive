---
title: "No Sound From Virtual MIDI Keyboard"
date: 2012-07-11
forum: Ubuntu Studio
---

### Post by Ikesurmarth on 2012-07-11
Hi, I'm new to the Ubuntu Forums and would like to ask this question:

I just installed Ubuntu Studio 12.04 64-bit in a virtual machine yesterday and there *is* sound. But when I open Virtual MIDI Keyboard, I get no sound from it! This *isn't* the first version of Ubuntu I've used, so I may be an intermediate now. Anyone who can help me?

---

### Post by WalmartSniperLX on 2012-07-11
Probably has to be patched to a synth since it is just a keyboard interface. Honestly, I don't know how this one works yet as I've not much time to mess with 12.04. If you want something to work with that offers instruments, try this synth:

```
sudo apt-get install zynaddsubfx
```

It has a keyboard built in. Just make sure you have jack running and routed propery to your system audio of choice.

---

### Post by hamnstar on 2012-07-11
Are you familiar with jack?  Jack is effectively a connection bay, you would use it to connect the output of your virtual keyboard to the input of a sound generator - also, you need to connect the output of the sound generator to your system's audio output, although this is usually done by default.

I usually use hexter (comes default with ubuntu studio) when im just trying to see if my audio/MIDI is working, as it has a very minimal GUI and has a big "Send test note" button to make sure your audio is actually working.

My apologies if you already knew this and your problem is deeper rooted:D

---

### Post by Chiel92 on 2012-07-26
> **WalmartSniperLX said:**
> Probably has to be patched to a synth since it is just a keyboard interface. Honestly, I don't know how this one works yet as I've not much time to mess with 12.04. If you want something to work with that offers instruments, try this synth:

```
sudo apt-get install zynaddsubfx
```It has a keyboard built in. Just make sure you have jack running and routed propery to your system audio of choice.

This might indeed be the problem. I would recommend using patchage to route applications, instead of qjackctl. The interface is more userfriendly, it works great, looks good, covers both JACK and ALSA and comes with ubuntu_studio by default.

---

