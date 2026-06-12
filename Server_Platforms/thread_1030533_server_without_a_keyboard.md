---
title: "server without a keyboard"
date: 2009-01-04
forum: Server Platforms
---

### Post by happyhacker on 2009-01-04
I have taken the keyboard and screen away because I control the server via a browser over the network. I have just realised why I cannot access it for the 1st time doing this - The startup stops when it finds no keyboard in the P/S2 socket.

Does anyone know a way round this (without plussing in a spare keyboard (maybe a doctored p/s2 plug or something)?

---

### Post by skern03 on 2009-01-04
> **cantthinkofanickname said:**
> I have taken the keyboard and screen away because I control the server via a browser over the network. I have just realised why I cannot access it for the 1st time doing this - The startup stops when it finds no keyboard in the P/S2 socket.

Does anyone know a way round this (without plussing in a spare keyboard (maybe a doctored p/s2 plug or something)?

This isn't exactly what it seems you wanted, but I use a KVM switch. If your server and other machine aren't close that won't work too well.

---

### Post by TestDummy! on 2009-01-04
Most BIOS' I've seen have an option in the CMOS setup to ignore halting the system if a keyboard isn't found when booting.

---

### Post by thanatoast on 2009-01-04
Check your BIOS settings.  Sometimes there is an option to halt on various failures or not.

---

### Post by skern03 on 2009-01-04
> **thanatoast said:**
> Check your BIOS settings.  Sometimes there is an option to halt on various failures or not.

TestDummy, thanatoast: Good catch - I'd forgotten about that. Thanks for prompting me to look! 

OP: Even on my relatively old BIOS (circa y2k), there are several options for Halt that ought to work: 
[LIST]
[*]All, but keyboard
[*]All, but keyboard/diskette
[*]No errors (in other words, blow right past)
[/LIST]

---

### Post by Krupski on 2009-01-04
> **cantthinkofanickname said:**
> I have taken the keyboard and screen away because I control the server via a browser over the network. I have just realised why I cannot access it for the 1st time doing this - The startup stops when it finds no keyboard in the P/S2 socket.

Does anyone know a way round this (without plussing in a spare keyboard (maybe a doctored p/s2 plug or something)?

In the machine's BIOS setup, there should be an option for "Report Keyboard Errors" that you can set to "ON/OFF" or "IGNORE".

Don't know exactly how it will be worded, but it should be obvious when you see it.

-- Roger

---

### Post by Iowan on 2009-01-04
If it helps, I had a '486 with this setting buried under "server settings" although machine is a desktop. I also have a program at work called NOF1 (or something similar) - but it was a .exe program (might still work w/ DOS boot disk). I think it was for a Compaq.

---

### Post by happyhacker on 2009-01-07
That's great, thanks I will investigate.

---

