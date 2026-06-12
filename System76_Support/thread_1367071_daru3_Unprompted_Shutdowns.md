---
title: "daru3 Unprompted Shutdowns"
date: 2009-12-29
forum: System76 Support
---

### Post by AlexInBlack on 2009-12-29
I'm running Xubuntu 9.10/Windows XP.

The problem first occurred about 3 days ago. I booted into Xubuntu and opened a .rtf file (that I had opened before)e While it was launching, I decided to disable wireless and lower screen brightness to save power. However, I accidentally pressed Fn+F4, which I think is sleep, instead of Fn+F8. I immediately pressed it again in a panic when I realized I'd pressed the wrong key. I then opened and closed the screen and then hit the mouse to log back in.
Almost immediately after I did this, the laptop just shut off. I tried booting again, getting beeping and the 2nd and 3rd indicator lights to the left (lock symbol and lock symbol with A, respectively) blinking. I got past the login screen before the daru3 again shut off. This happened repeatedly as I continued to attempt booting up, but with the shutoffs occurring progressively earlier in the bootup sequence, the middle shut-offs occurring during automated disk checks.
In a fit of desperation, I decided to boot into my Xubuntu LiveUSB. It worked, and continued to do so after I rebooted into the installed Xubuntu.

That is, until now. I again had just booted up and was launching all the apps I wanted open when the daru3 just shut off. I tried rebooting into the installed Xubuntu, eliciting the beeping and blinking indicator lights, and was cut off during the disk check. I then tried the LiveUSB Xubuntu, but it failed during the glowing mouse pre-login loading screen. I then tried Windows XP, which failed while all the start-up apps were launching.

Does anyone know why this is happening? My first guess would have been heat, since I had the daru3 on my lap the first time, while I was in a car, but this second time around, I had it on a cooling pad. The daru3 had about 40% battery charge the first time and the 2nd time, was on the AC adapter.

---

### Post by in0giro on 2009-12-29
just a quick thought: is the RAM and AC plug seated properly?  maybe when you panicked something got loose?

---

### Post by AlexInBlack on 2009-12-29
I wouldn't know how to check if the plugs are seated properly. My guess is that the AC adapter plug is seated properly since during the few minutes I'm booted in, the battery utility readily detects when the AC adapter is plugged in.

---

### Post by in0giro on 2009-12-30
> **AlexInBlack said:**
> I wouldn't know how to check if the plugs are seated properly. My guess is that the AC adapter plug is seated properly since during the few minutes I'm booted in, the battery utility readily detects when the AC adapter is plugged in.

perhaps try wiggling the AC plug a bit and see if it shuts off.  otherwise, could be a memory problem?  have you run Memtest86+ yet?

  good luck.

---

### Post by thomasaaron on 2009-12-30
If you haven't already, please shoot me an email (support...at...system76...dot...com), and I'll walk you through some things. In a nutshell, we need to reseat the RAM, the hard drive and reset the CMOS. It's all pretty easy to do.

---

