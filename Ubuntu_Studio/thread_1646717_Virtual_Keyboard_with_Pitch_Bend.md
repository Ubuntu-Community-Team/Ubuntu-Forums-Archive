---
title: "Virtual Keyboard with Pitch Bend"
date: 2010-12-16
forum: Ubuntu Studio
---

### Post by K.J. on 2010-12-16
I've been using vmpk as a Virtual MIDI keyboard. Is there a way to map the pitch bend to a keyboard press or mouse scroll? I've been looking for a way, but have been unable to find it. If not, does anyone know of a virtual keyboard that supports this? I don't need a lot of features, just translation of key presses to notes and pitch bend that create a midi signal (that I can feed into qSynth).

Here's what I'm doing, in case anyone knows a better way of doing it, but it's been working well so far. I use my laptop as a synth with a keyboard midi controller. I'm using the real time kernel and connecting the midi input to qsynth with jack. I also sometimes control the synth with an xbox rock band controller. I'm using xboxdrv to create a joystick, then qjoypad to create keyboard presses from the joystick. I then have vmpk capturing those presses and converting into midi, which I can then feed back into qsynth.

Thanks!

---

