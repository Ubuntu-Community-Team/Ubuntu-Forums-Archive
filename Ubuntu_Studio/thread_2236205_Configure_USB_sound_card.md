---
title: "Configure USB sound card"
date: 2014-07-25
forum: Ubuntu Studio
---

### Post by davstar on 2014-07-25
Hello 
i don't know- if anyone knows --but if someone does know how to configure a USB sound card in Ubuntu studio through the terminal with commands?? I have a M-audio fast track pro and i am running Ubuntu studio 14.04 on my Lap top the sound card shows up in the sound configuration menu  and i can even get sound out of it - it's just a matter of getting sound in through the USB card that i can't seem to do for some reason - I don't know if i'm missing something or what but i have not been able to record anything in Ubuntu studio With the M-Audio sound card. Does anyone know How i could configure my sound card from Terminal?? maybe? any help is appreciated

[ATTACH=CONFIG]255029[/ATTACH][ATTACH=CONFIG]255030[/ATTACH][ATTACH=CONFIG]255031[/ATTACH]

---

### Post by gdesilva on 2014-07-25
Give this a go....

1. Click Volume Control - the one you have shown above
2. Click on the Playback tab - your first image is showing the Input tab
3. You should see two entries just like in your first diagram - one for built in audio and one for M-Audio
4. Click on the 'tick' (in green) sign on the M-Audio card - this should make it go grey and has the effect of making it your default audio device.
5. Also make sure that the card is not muted - the first button is not clicked.

Test your audio now.

If you want to do this on a terminal the command you need is alsamixer.

---

### Post by jejeman on 2014-07-26
> How i could configure my sound card from Terminal?? 
Ah, that mighty terminal...

Which application are you using to record sound?
Turn off internal card in BIOS, and look, everything goes via USB card. ;)

---

