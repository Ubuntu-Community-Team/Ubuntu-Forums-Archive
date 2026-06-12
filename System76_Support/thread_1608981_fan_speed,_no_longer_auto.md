---
title: "fan speed, no longer auto"
date: 2010-10-29
forum: System76 Support
---

### Post by supersonicdarky on 2010-10-29
On my panp7, the fan stopped adjusting speed according to cpu temp. I think it happened after I (accidentally) pressed the silent mode button. Ever since, the button only toggles between loud and very loud. Since I can do this before getting into the os (debian) I don't think this is a software problem (linux anyway). I also tried booting from an ubuntu usb to the same effect.

I looked in the bios but it has almost no options, and certainly none regarding fan speed.

Am I missing something here? Noise is an issue that needs fixing.

---

### Post by paalvibe on 2010-12-29
I'm seeing exactly the same issue, from around December 10th. Not sure what activated it. Stuff I did right before it started happening which might be related:

1. installing laptop-mode-tools
2. sleeping the machine
3. doing apt-get upgrade 

Kubuntu version 10.04.1
Machine:
Pangolin Performance (PAN-P7)
Display Resolution 15.6" HD+ LED Display with Super Glossy Surface (1600 x 900)
Processor Core i7-740QM Processor ( 45nm, 6MB L3 Cache, 1.73GHz)
Memory 8 GB - DDR3 1333 MHz - 2 DIMMs This option available with Intel Core i7-740QM or Core i7-840QM CPU
Graphics ATI Mobility Radeon HD 4570 Graphics with 512MB GDDR2 Memory
Hard Drive 320 GB 7200 RPM SATA II

---

### Post by isantop on 2010-12-29
What effect does the silent mode button have on your laptop. Is it like the original poster, where it simply isn't as quiet as it used to be, but still functions okay?

---

### Post by paalvibe on 2010-12-30
A possible fix/workaround for this: In the top left corner of the keyboard there are three buttons. One of them is "M". If you press this the laptop toggles between performance/noisy mode and silent mode.

---

