---
title: "Troubleshooting midi keyboard/cable/software"
date: 2011-11-23
forum: Ubuntu Studio
---

### Post by hreichgott on 2011-11-23
Hi,

I have a Yamaha P60 which up till now has mostly been a great audio recording device (I made my cd of ballet class music on it). I'm getting more into MIDI on Linux and would like to use the piano's MIDI capability to record.

I bought some inexpensive MIDI-USB cables. I tried recording and playback in Rosegarden, LMMS, and Jack with the Foo organ synthesizer. Rosegarden, LMMS and JACK can all see the keyboard and allow it to be chosen as a recording and playback device. None of them record MIDI events from it or send MIDI events to it.

Any suggestions on what to try next? I have never used this piano for MIDI before, and the cables are new. I already tried swapping IN and OUT on the cables (I am still not sure if IN on the cable means "into the piano for playback" or "into the computer for recording"...)

Software MIDI works fine on Rosegarden etc. entering notes one by one into the notation or piano roll editor.

---

### Post by jejeman on 2011-11-23
Connect the keyboard via usb, and do
```
lsusb
```
give us the output
Keyboard (or something related, i don't know about those midi-usb cables) must be listed, otherwise, it wont work.
Here is sample output from my system
```
Bus 002 Device 002: ID 0944:010d KORG, Inc. nanoKEY MIDI keyboard
```
"MIDI out" on keyboard sends midi data. "Midi in" recives midi data into the keyboard.

---

### Post by hreichgott on 2011-11-23
```
Bus 003 Device 005: ID 0a92:1010 EGO SYStems, Inc. RoMI/O

```

In the sequencers' windows it shows up as VIEWCON MIDI 1.

---

### Post by hreichgott on 2011-11-23
PS I understand what in/out means on the keyboard, I'm just not sure what it means on the cable. (ie does the "in" cable go into the "in" port on the keyboard, which would mean providing input to the keyboard, or is it vice versa which would mean providing input to the computer?)

---

### Post by jejeman on 2011-11-23
It's recognized, and looks like it's suported by alsa, as it shows up as you say.
Try first something simple. Like just to connect keyboard with simple soft synth, like phasex.

---

### Post by sgx on 2011-11-25
> **hreichgott said:**
> PS I understand what in/out means on the keyboard, I'm just not sure what it means on the cable. (ie does the "in" cable go into the "in" port on the keyboard, which would mean providing input to the keyboard, or is it vice versa which would mean providing input to the computer?)

You'll know when you've got it backwards :popcorn:

Typical computer geekery, midi out goes to midi in, and
midi in goes to midi out. I resorted to colored tape
on the cables, and the proper locations on the keyboards
and audio interfaces.

Line-out and headphone out go to line-in. Some headphone
outputs are much better than others, and are both quiet,
and have gain control, useful for crazed high-gain amp-sim
freeks, to whom 10 is the most evil and limiting of numbers. :)

---

