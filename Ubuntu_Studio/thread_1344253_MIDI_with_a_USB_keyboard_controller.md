---
title: "MIDI with a USB keyboard controller"
date: 2009-12-02
forum: Ubuntu Studio
---

### Post by emu42 on 2009-12-02
I have an M-Audio KeyStudio 49 USB keyboard, which I'm trying to get set up with a software synth. I tried using MIDI in Jack/ZynAddSubFx and LMMS (by itself). Both times, I've been able to get the keyboard to trigger notes, but each note is sustained. Once I press a key, the notes just stays at full volume until I close the program, making it useless. What's happening here?

---

### Post by AutoStatic on 2009-12-03
Hello Emu42, what are your current JACK settings? And what is the outcome of **lsusb** in a terminal with the M-Audio attached? And what if you try with a virtual keyboard (package *vkeybd*)?

---

### Post by emu42 on 2009-12-03
Actually after trying to restart with the keyboard attached, my system wouldn't restart and I had to install a new kernel, with which Jack doesn't work anymore. I'm still trying to figure out that one. Though LMMS is still producing MIDI by itself.

Results of lsusb:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0763:019c Midiman KeyStudio
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Also, I've been using the virtual keyboard for a while with great results, since I haven't had a keyboard.

Thanks for your help!

---

### Post by AutoStatic on 2009-12-03
> **emu42 said:**
> Bus 003 Device 002: ID 0763:019c Midiman KeyStudioThanks for the output! It's being recognized properly. And what does **amidi -l** say? It should give back the port number the M-Audio is using. With **amidi -p portnumber-M-Audio -d** you can verify what happens when you press a key. Normally it should spit out two hex codes when you press a key, one when you press the key and one when you release it. What happens in your case then?

I've attached a screenshot with an example of how it could look like. I don't have a MIDI keybaord at hand so I used a virtual keyboard and a virtual MIDI port.

---

### Post by emu42 on 2009-12-03
I tried amidi -l, but I'm not sure this is what I'm supposed to get, because it doesn't have the port number.

Dir Device    Name
IO  hw:0,0    CA0106 MPU-401 (UART)
cannot get rawmidi information 2:0: No such file or directory

In the Jack connections, I tried connecting the keyboard to Timidity, which I had to killall in order to get the sound to stop, so that didn't work. I noticed you had your keyboard connected to a program called client 129, is that of any significance?

---

### Post by kayosiii on 2009-12-04
Sounds like sustain is being switched on... Sustain is usually mapped to CC64 if anything were to set that CC to 127 (maximum) value Zyn would behave in the way you describe.

---

### Post by emu42 on 2009-12-04
Actually that sounds about right, and the keyboard does have an input for a sustain pedal but I don't have one. Do you know how I can set the CCs with software?

---

### Post by kayosiii on 2009-12-05
> **emu42 said:**
> Actually that sounds about right, and the keyboard does have an input for a sustain pedal but I don't have one. Do you know how I can set the CCs with software?

Not having the connection should send an 0 to that CC, However in Zyn you can switch off hardware control for sustain by hitting the controllers button.

---

### Post by emu42 on 2009-12-05
It took a good amount of tweaking, but I finally got it to work. Thanks to both of you!

---

