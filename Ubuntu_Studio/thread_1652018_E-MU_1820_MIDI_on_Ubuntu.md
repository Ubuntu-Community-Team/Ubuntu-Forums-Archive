---
title: "E-MU 1820 MIDI on Ubuntu"
date: 2010-12-24
forum: Ubuntu Studio
---

### Post by marcoharder on 2010-12-24
Still having a problem with MIDI on this card. It records well, and picks up the midi signal [as evidenced by the light on the Audiodock] but it doesn't go into the system to be fed into say, QSynth. Anyone who could help out?

---

### Post by Pablo_F on 2010-12-24
Hi, 

Could you give the terminal output of the following informative commands with qsynth running?

arecordmidi -l
aplaymidi -l
jack_lsp -c

Cheers, Pablo

---

### Post by cchhrriiss121212 on 2010-12-24
In [another thread ]("http://ubuntuforums.org/showthread.php?t=1623948&highlight=emu+0404&page=2")it was determined that the EMU 0404 requires 48kHz samplerate in order for MIDI to work properly. Your card should be the same as it uses the same driver, if you can verify this I will add another note to the [ALSA Creative]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs") page.

---

### Post by marcoharder on 2010-12-25
> **Pablo_F said:**
> Hi, 

Could you give the terminal output of the following informative commands with qsynth running?

arecordmidi -l
aplaymidi -l
jack_lsp -c

Cheers, Pablo

Here are the outputs: 
arecordmidi -l
 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
 16:0    E-mu 1010 [MAEM8810]             Audigy MPU-401 (UART)
 16:32   E-mu 1010 [MAEM8810]             Audigy MPU-401 #2

aplaymidi -l
 Port    Client name                      Port name
 14:0    Midi Through                     Midi Through Port-0
 16:0    E-mu 1010 [MAEM8810]             Audigy MPU-401 (UART)
 16:32   E-mu 1010 [MAEM8810]             Audigy MPU-401 #2
 17:0    Emu10k1 WaveTable                Emu10k1 Port 0
 17:1    Emu10k1 WaveTable                Emu10k1 Port 1
 17:2    Emu10k1 WaveTable                Emu10k1 Port 2
 17:3    Emu10k1 WaveTable                Emu10k1 Port 3
129:0    FLUID Synth (Steinway)           Synth input port (Steinway:0)
130:0    FLUID Synth (Steinway)           Synth input port (Steinway:0)
131:0    FLUID Synth (Drums)              Synth input port (Drums:0)
132:0    FLUID Synth (Drums)              Synth input port (Drums:0)

jack_lsp -c
system:capture_1
system:capture_2
system:capture_3
system:capture_4
system:capture_5
system:capture_6
system:capture_7
system:capture_8
system:capture_9
system:capture_10
system:capture_11
system:capture_12
system:capture_13
system:capture_14
system:capture_15
system:capture_16
system:playback_1
   Qsynth_Steinway:l_00
   Qsynth_Steinway-01:l_00
system:playback_2
   Qsynth_Steinway:r_00
   Qsynth_Steinway-01:r_00
Qsynth_Steinway:l_00
   system:playback_1
Qsynth_Steinway-01:l_00
   system:playback_1
Qsynth_Steinway:r_00
   system:playback_2
Qsynth_Steinway-01:r_00
   system:playback_2

---

### Post by marcoharder on 2010-12-25
Okay, so now I've switched it to 48khz and MIDI is working...only on the second MIDI port at the back of the EMU Audiodock. Port 1 in front still doesn't work. :(

---

### Post by marcoharder on 2010-12-29
Any help?

---

### Post by Alexandre J. on 2011-04-29
I'm sorry to update this thread but I have actually the same card (E-MU 1820) and I have no sound on Ubuntu 11.04. I see you have MIDI problem, then you have basic sound ? Did you install something ? Drivers ? I just want to use Ubuntu for desktop application, no MAO.

And it's strange because, when the ubuntu's setup have been done, I'm sure I have listened welcome sound. And now, nothing...

Thank you !

If an administror prefer, I can create a new thread.

---

### Post by Alexandre J. on 2011-04-29
Hello,
Finally I find a solution (not found before) !

[http://timhodson.com/e-mu-1820-and-ubuntu/]("http://timhodson.com/e-mu-1820-and-ubuntu/")

---

