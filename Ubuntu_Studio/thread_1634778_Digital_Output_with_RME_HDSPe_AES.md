---
title: "Digital Output with RME HDSPe AES"
date: 2010-12-01
forum: Ubuntu Studio
---

### Post by solo16 on 2010-12-01
Dear all,

I'm using RME Hdspe AES (PCIe) however I try to configure Jack for digital output however it couldn't seems have any setting specify for digital output I can only see analogue which my interface card don't have. 

Could anybody shed some light on me, of how to configure Ubuntu Studio for audio playback with digital output?

I also tried Audacious and played a wav audio file, it works with no error msg pop up, however I couldn't hear anything from my speaker.

Please kindly be gentle here as I'm new to linux with 0 knowledge at all! If possible could anyone please provide step-by-step instructions!

Many Thx!!!!

---

### Post by cchhrriiss121212 on 2010-12-01
Could you post the output of "aplay -l" from a terminal? (Go to Accessories>Terminal, then type the command and press enter). This will check your card is correctly recognised.

I have not used jack with digital output, but I imagine it does not need any setting adjustments as any potential digital-analogue conversion will be handled by the sound card and not jack.
> I can only see analogue which my interface card don't have
Where is it that you see this?

---

### Post by solo16 on 2010-12-03
Hi sorry for getting to you so late. 
[IMG]file:///home/solo16/Desktop/Screenshot.png[/IMG]Here I attached the aplay screen. 

Also I tried to use hdspmixer, but it can't be opened. I clicked but nothing pop up.

Thx for your help!

---

### Post by solo16 on 2010-12-06
Problem solved!!! Found out that on default the alsamixer is muted on the output channel.

---

