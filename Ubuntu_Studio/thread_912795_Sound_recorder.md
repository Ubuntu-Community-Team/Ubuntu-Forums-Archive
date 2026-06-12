---
title: "Sound recorder"
date: 2008-09-07
forum: Ubuntu Studio
---

### Post by ingeva on 2008-09-07
New to Ubuntu. Running 8.04 Hardy.

My soundcard:
```
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff4000 irq 22
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfdefc000 irq 23
```

Three questions:

I can record from the microphone but not from line input. The choices are
"Front mic boost"
"Mic boost"
 "Capture"
    "Capture 1"
"Digital"
"Digital" is silent; all the others evidently use the microphone. How do I blow life into the line input?

I have installed a volume meter/monitor but I can't find the program. Where the H*** i ist?

Is there any way to get playback while recording?

---

### Post by ingeva on 2008-09-07
> **ingeva said:**
> Three questions:


The first and third are solved: There was no output from the medium I connected to Line Input -- and there's no playback when recording, but I can listen to the input signal, which is nearly as good.

Capture works, Capture 1 works better.

So the second question is still  looking for an answer:

Where is the recording monitor that I installed? The description didn't tell, and it does not appear in the gnome menu.

---

### Post by ellgor on 2008-09-15
Hi,

It sounds like a plugin you have downloaded, which means it needs a main program to work from/in if you follow that, I can recommend Ardour if you want a decent recording setup, hope this helps.

Regards, Ellgor.

---

### Post by ingeva on 2008-09-16
> **ellgor said:**
> Hi,

It sounds like a plugin you have downloaded, which means it needs a main program to work from/in if you follow that, I can recommend Ardour if you want a decent recording setup, hope this helps.

Regards, Ellgor.

Thanks!

I found ubuntustudio-audio, which has everything I want and more! :)
Ardour was also installed with that.

---

