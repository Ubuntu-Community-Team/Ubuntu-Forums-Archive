---
title: "kernel 3.8.0-14  : bad output sound"
date: 2013-03-23
forum: Ubuntu Development Version
---

### Post by dino99 on 2013-03-23
ALC882 HDA Intel chip

get a noisy "generic" sound output with that new kernel. Its a regression as the previous kernels works. What is new with that one : System Settings Sound has nothing listed (empty), so the hardware is not monitored.

how is sound on your system with 3.8.0-14 ?

---

### Post by Harry33 on 2013-03-23
> **dino99 said:**
> ALC882 HDA Intel chip

get a noisy "generic" sound output with that new kernel. Its a regression as the previous kernels works. What is new with that one : System Settings Sound has nothing listed (empty), so the hardware is not monitored.

how is sound on your system with 3.8.0-14 ?

Sound is fine here on my 64-bit desktop.
I use Realtek ALC889A sound card.
What is your sound card?

---

### Post by zika on 2013-03-23
> **dino99 said:**
> ALC882 HDA Intel chip

get a noisy "generic" sound output with that new kernel. Its a regression as the previous kernels works. What is new with that one : System Settings Sound has nothing listed (empty), so the hardware is not monitored.

how is sound on your system with 3.8.0-14 ?You've made me peek into the abyss of propsed... No, sound is OK even with -14...
Did You check udev upgrade?

---

### Post by dino99 on 2013-03-23
i was out for a while, so a cold boot later, that ALC882 chip is detected (can change the settings via the sound icon into System Settings) but when i start a sound stream (radiotray for example), i need to change the profile choice (analog output -> profile  -> surround 4.0 -> surround 4.1) to get it activated.

Thats it, i will see on the next boot if the sound chipset is detected (as now) or not (as the previous boot); seems erratic.

note: the 3.8.4 kernel changelog has "ALSA: seq: Fix missing error handling in snd_seq_timer_open()"
seems it has something to do with my sound issue. 

note2: looking at 3.9 kernel changes, i'm seeing that:
"ALSA: hda - Fix typo in checking IEC958 emphasis bit"

this is how that sound onboard chip is identified (numeric choice). So i need to test that vanilla one.

---

### Post by deri on 2013-03-23
Take contact with the kernel developers as soon as you figure out what's the kernel which has the bug.

---

### Post by jerrylamos on 2013-03-24
Acer Aspire 1 netbook with:
Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
sound O.K. with 3.8.0-14 from BBC video.  Now that's hardly a high definition source.....

---

### Post by kevpan815 on 2013-03-24
So far the only problem that I have had with 3.8.0.14 is the fact that Today's Build Failed the UEFI Security Check A.K.A. SecureBoot.

---

### Post by dino99 on 2013-03-25
Well, as i also use the gnome3-team ppa on that system, now the sound driver activation is well done; so i suppose that package(s) transition was to blame.

---

