---
title: "Which USB MIDI driver do I need."
date: 2008-11-17
forum: Ubuntu Studio
---

### Post by groundnut on 2008-11-17
I'm planning to buy an Yamaha KX-49 keyboard (controller).

I would like to connect the keyboard via USB.

Which USB MIDI driver can I use for Ubuntu?

---

### Post by raboofje on 2008-11-22
> **groundnut said:**
> I'm planning to buy an Yamaha KX-49 keyboard (controller).

I would like to connect the keyboard via USB.

Which USB MIDI driver can I use for Ubuntu?

With my M-audio keystation and midisport 2x2, it was just a matter of plugging it in, and connecting it with qjackctl - no further configuration needed.

I guess it uses the snd-usb-audio module as a driver, but I haven't had to fiddle with any of that manually.

---

### Post by groundnut on 2008-11-23
Thanks raboofje.

So with a little luck my Yamaha KX-49 (keyboard/midi controller) will work out of the box.

---

### Post by raboofje on 2008-11-23
> **groundnut said:**
> So with a little luck my Yamaha KX-49 (keyboard/midi controller) will work out of the box.

Jep. You'll have to hook up some program to make the sounds of course, like ZynAddSubFX, timidity or QSynth.

---

### Post by groundnut on 2008-11-23
I have already installed and used Rosegarden, ZynAddSubFX, Hydrogen and Hexter.
But so far I used the mouse to play music (with ZynAddSubFX).
I programmed Hydrogen.
I transferred a MIDI file from Cubase to Rosegarden and let Hexter play the part.

Now I want to play ZynAddSubFX and Hydrogen from Rosegarden instead of standalone. 
@raboofje   Do you know how that works?

---

