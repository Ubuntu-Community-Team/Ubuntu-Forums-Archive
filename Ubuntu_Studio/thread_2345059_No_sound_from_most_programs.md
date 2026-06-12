---
title: "No sound from most programs"
date: 2016-11-30
forum: Ubuntu Studio
---

### Post by DavidS on 2016-11-30
I am running Ubuntu Studio 16.04 on an HP laptop.  Using Jack I can get sound from Qtractor etc.

But I can't get any sound at all from programs such as Chrome, VLC etc. which Jack doesn't recognize (or vice versa).

I have tried with pulseaudio active and with it killed.

Also when I click on the "All settings" icon, I see most of the expected items such as Display, Keyboard, Printers etc. etc., but there is no entry for Sound or anything similar.  Equally I have no sound icon in the panel at the top of the screen.  I can run alsactrl in a terminal, however.

In QjackCtl I have input and output sources set to hw:Generic which is HD-Audio Generic (hw:1).  Using this I can get sound via Jack through the computer speakers or headphones, but not from VLC etc..

The other main option is hw:HDMI which says HDA ATI HDMI (hw:0).  The computer has an HDMI socket, but when I have tried connecting this to a TV I still get no sound.  In any case, I don't generally want to use the HDMI output.

Using alsamixer I have lots of controls for input and output volumes if I select Sound Card 1 (HD-Audio Generic), but if I select Sound Card - (default) or Sound Card 0 (HDA ATI HDMI) I just get a little square in the middle of the screen showing "00" and labelled "S/PDIF".

Can anyone suggest how I can get sound working generally (not just for specialized programs) on this computer?

David

---

